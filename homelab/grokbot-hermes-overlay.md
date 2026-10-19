# Grok Bot ↔ Hermes over NetBird (no public IP)

Planning note. Overlay-only. Nothing enabled yet.

**Goal:** Grok Bot can ask Hermes without a public address, Funnel, Traefik, or Tailscale. Grok Bot never gets Hermes’ toolbox — only a tiny pipe.

**Not in this note:** RustDesk, Discord-as-relay, work-laptop / dashboard-in-a-browser, CX23 Traefik.

**Current state**

- NetBird client is on the Grok Bot VM; setup key not used yet.
- Hermes webhook platform is off; `:8644` is closed on pi-hermes.
- Dashboard `:9119` is overlay-reachable (HTTP 302). That is *not* the pipe.
- You apply NetBird (groups, keys, policies). Do not change the dashboard or VPS until you say go.

---

## Shared (both options)

Same mesh, same risk idea, same “no public IP.”

- Tighten `All → All` **before** the peer exists.
- Enroll the VM: group `grokbot`, one-use setup key, that group only, management `https://netbird.motogringo.productions`. Hostname `grokbot`. Revoke the key after it appears.
- Policy **after** the peer exists: `grokbot` → `pi-hermes`, **one TCP port**, one way. No NAS, no SSH, no Lemonade, no extra hosts.
- Bind the Hermes-side listener to **`wt0` / overlay IP only**, never `0.0.0.0` / LAN / public NIC.
- HMAC (or equivalent) in `.env` — never in chat, never on VPS Traefik.
- Two-tool *idea*: Grok Bot can only poke the pipe. Hermes still runs the job on the Pi. Use a **stripped profile** (tight toolsets, no ERP/vault skills) or this is theater.
- Proof from the VM: `netbird status`, MagicDNS (`pi-hermes.netbird.selfhosted`), then `curl` health.

If Grok Bot’s MCP client is **Remote HTTPS** (Cursor/xAI cloud fetches a URL), overlay never gets a packet. Cloud cannot resolve `*.netbird.selfhosted`. Overlay only works if the client is **on the enrolled VM** (or a fragile “route traffic through this desktop” setup).

---

## Option A — Hermes webhooks

Stock Hermes. Grok Bot talks HTTP over the overlay.

```
Grok Bot VM  --NetBird-->  pi-hermes:8644  (HMAC)
```

| | |
|---|---|
| Surfaces | `GET /health`; one HMAC-signed `POST` that starts a run |
| Grok Bot UX | `curl` or a small script. Not a native tool. |
| Answer | Job + deliver/poll. Not a tool result in the Grok Bot chat unless we stretch it. |
| Auth | HMAC Hermes already has |
| Timeout | Run can outlive the POST |
| Build | Enable webhook platform, pin bind to `wt0`, one route, HMAC. No new server. |
| Port / policy | TCP **8644** |

Default webhook listen is dual-stack all interfaces. That is a LAN footgun. Pin overlay.

---

## Option B — Custom MCP (Command on the VM)

Same overlay and HMAC idea; Grok Bot gets named tools. **Not** a fork of the public OAuth / Streamable-HTTP gateway.

```
Grok Bot chat
  → stdio MCP on the VM   (hermes_ask, hermes_status)
      → NetBird
          → Pi HMAC HTTP on wt0
              → hermes chat -q … --oneshot -Q   (stripped profile)
```

| | |
|---|---|
| Surfaces | `hermes_status` → overlay `/health`; `hermes_ask` → overlay `/ask` |
| Grok Bot UX | Tools in the Grok Bot chat; reply is a tool result |
| Answer | Sync oneshot (`hermes chat -q --oneshot -Q` is real on this install) |
| Auth | HMAC we implement. No OAuth / PKCE / DCR. |
| Timeout | Grok Bot MCP ~**60s**. Long jobs need extra tools later. |
| Build | Two small programs we own: VM stdio FastMCP + Pi HMAC listener on `wt0` |
| Port / policy | One TCP port for `/health` + `/ask` (not 8644 unless we reuse it) |
| Load in Grok Bot | **Custom MCP → Command** on the computer. Never Remote HTTPS. |

Do not put TLS/OAuth in front of MagicDNS. WireGuard already encrypts. Do not put `/mcp` on CX23 Traefik.

---

## Pros / cons

| | Webhook (`:8644`) | Custom MCP (Command on VM + `/ask` on Pi) |
|---|---|---|
| What Grok Bot sees | `curl` / a script | `hermes_ask` / `hermes_status` in chat |
| Answer comes back | Job + deliver/poll | Sync tool result |
| Build / maintain | Stock Hermes + overlay bind | Two programs we own |
| Auth | HMAC (built-in) | HMAC we write |
| Timeout | Run can outlive the POST | ~60s MCP; long jobs need more tools |
| Failure surface | Gateway + route config | Our code, FastMCP, Grok Bot Command MCP |
| Bind footgun | Default all-interfaces — must pin `wt0` | Same, because we’d write the listener |
| Remote HTTPS trap | None | Easy to misconfigure as cloud MCP and “need a public URL” again |
| Matches “two tools” | Same *risk*. Worse *UX* | Same *risk*. Better *UX* |
| When the VM is down | Dead | Dead |

**Safety is the same class.** MCP does not jail Hermes; a stripped oneshot profile does. Webhook with `--skills` / a dedicated profile is the same control.

**No public IP either way.** MCP stays overlay only as Command-on-VM.

---

## Call

- **Webhook** if the goal is a low-risk overlay pipe with almost no new code. House-shaped.
- **Custom MCP** if Grok Bot must *use tools named ask/status* and see Hermes’ reply in that turn. Extra software for chrome, not for safety.

Do not build MCP until the mesh is proven (`netbird status` + overlay `curl`). If `curl` is enough, skip MCP.

---

## Order (when we actually do it)

1. You: tighten `All → All`, enroll `grokbot`, policy to **one** TCP port.
2. Proof from the VM: MagicDNS + health `curl`.
3. Then either enable webhooks on `wt0`, or write the two MCP programs. Not before.

No clone of public MCP gateways. No Funnel. No Tailscale. No listeners until go.
