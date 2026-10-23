# Session skills on Hermes

Design note only. No skills are installed. Nothing in this file is a vault edit.

The three Claude skills were one memory loop. Start pulls the trail into a new chat and opens a new file. Log writes decisions, dead ends, blockers, and open questions while the chat is still alive. Close compiles that into a briefing the next session, and the human, can use. The project doc changes only when a Pending Merge item is promoted by hand.

The reasons to keep that loop: the model cannot hold the trail once the window fills or a new chat starts, and the human should not have to. The vault file is the shared copy. This chat can use it. It must not be the only place the trail exists.

## What not to copy

Do not port the Obsidian MCP tools, the frontmatter quoting workaround, or the instruction to live inside the librarian. The working session stays on whichever profile the human is already in. Do not auto-edit the project doc. Do not treat a Hermes compaction as a substitute for the file.

## Where the skills live

Hermes skills are per profile. A skill on `default` is invisible to `librarian`, and the reverse. These do not belong in the Hermes git repo, and they do not belong on `mail`.

Two copies, two jobs:

- Working profile (`default`, and any later profile that actually does the work): three thin trigger skills, `session-start`, `session-log`, `session-close`. They never open `/home/chadsmith/vaults/brain`. They send one librarian one-shot and then talk to the human.
- Librarian profile: one writer skill, `session-vault`, with three procedures. The file rules live in one place. The one-shot names the operation.

Draft the skill text in this project folder when we build. Install with `skill_manage` into each profile. Installing on one profile does not install on the other.

Bot Mode is not required. A one-shot is the handoff. If Bot Chat messaging replaces the shell-out later, the contract stays the same: the working profile sends facts, the librarian writes, session metadata comes back.

## Librarian writes only

Possible, and it should be the rule.

The librarian is the only profile that reads or writes the vault for this loop. The working profile does not `read_file`, search, or patch anything under `~/vaults/brain`. It does not run `ob`. Continuous sync is already the host service `obsidian-sync.service`. The librarian does not start a second sync.

The catch: a librarian one-shot cannot see the working chat. Start can be done almost entirely on the librarian, because the trail is already in the vault. Log and close cannot. The working profile has to send the new facts. The librarian merges them into the file and does not invent any.

Session notes are the memory the next chat needs. The human has said they are metadata, not the secret material. This design assumes a start or close reply may include Current State, the decision trail, dead ends, the first next step, Carry-Forward, and the stub path. It must not include Reference bodies, client notes, or ERP content. The standing SOUL line is still path-only. Change that line when we install the skills, not before.

## How a turn runs

Stamp times in `America/Indiana/Indianapolis`, from the machine. Not `America/New_York`.

Pass the stub path forward. Start returns it. Log and close send it back. Do not hunt for "the active session" if the path is already known. If the human says "log this" in a chat that never started a session, the librarian uses the Projects Index, finds the most recent `status: active` file for that project, and stops to ask if two are active.

### Start

Working profile asks which project if none was named, then stops until it has a name. Librarian reads `_System/_Dashboard/Projects Index.md`, the project doc, and the latest session file. It reads `_System/Templates/session-template.md` at stub time and does not keep a second copy of the template in the skill. It writes the next session file. Session 1 leaves Next Steps and Carry-Forward empty. Later sessions copy Next Steps item 1 and Carry-Forward Context from the prior file. Other sections get placeholders.

The reply back is the briefing: current state, blockers, dead ends worth not repeating, first task, and the new path. The working profile shows that and waits. It does not start the first task.

For the rest of that chat, the working profile treats a decision, reversal, dead end, blocker, or open question as a log event. That standing rule lives in the working profile's start skill. The librarian never watches the chat.

### Log

If the message already says the type and the content, write it. Otherwise ask one question: decision, dead end, blocker, or open question. Then one librarian one-shot.

Librarian appends to the matching section. Decision rows are append-only. A reversal is a new row with Supersedes set. It does not edit or delete old rows. A blocker sets `has_blockers` and `status: blocked`. Resolving the last blocker sets them back. Confirm in one line, including the row number when there is one, and stop.

Do not log chatter. A cold Qwen one-shot per "ok" will feel broken. Batch minor notes. A real decision or a failed approach is worth the turn.

### Close

The working profile assembles what the conversation added: accomplished items, late decisions, missed dead ends, open questions, ordered next steps, pending-merge items, and carry-forward that is not already in the project doc. Current State is one paragraph a person could read after a week away. It sends that payload. It does not write the file.

Librarian reads the stub first so logged rows are not duplicated. It fills empty sections, leaves existing decision rows alone, computes `duration_minutes` from `session_start`, and sets `session_end`, `status`, `has_blockers`, and `next_action` (Next Steps item 1). Status is one of active, paused, blocked, complete. It writes that file only. Prior session files stay untouched. The project doc stays untouched.

Close Checklist stays unchecked. The human checks it in Obsidian. The reply flags Pending Merge items and tells them to start a new chat so the next start reads the file, not this conversation.

If the librarian cannot write, the working profile still has the payload. Say so and keep the text in the chat. Do not invent a second write path that touches the vault.

## Open points

- The SOUL path-only rule contradicts this design on purpose until we install the skills.
- The session template still says Claude maintains the file through MCP. That callout should be rewritten when the first stub is created here, by the librarian, not copied forward forever.
- `skills-strategy.md` was never in the vault. This note plus the three skill notes under `Projects/Claude Management/Skills/` are the record we have.
- A long close payload may be slow on Qwen. That is acceptable. Splitting close across several one-shots is worse, because a half-written session file is the failure the loop exists to prevent.
