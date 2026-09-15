# Claude plugin directory submission

Submit at https://clau.de/plugin-directory-submission (the community
marketplace, `anthropics/claude-plugins-community`, is a read-only mirror of
approved entries; pull requests there are closed automatically). Approved
plugins appear in Claude Cowork (claude.com/plugins) and install in Claude Code
with `claude plugin install banger@claude-community`. Once approved, the
directory re-pins to new commits on the public repo automatically.

Answers for the form:

| Field | Value |
| --- | --- |
| Plugin name | Banger |
| Plugin id | `banger` |
| Public repository | https://github.com/MuchBetterApps/banger-plugin |
| Manifest | `.claude-plugin/plugin.json` at the repo root |
| Marketplace | `.claude-plugin/marketplace.json` at the repo root (`banger@banger`) |
| Category | Productivity (email) |
| Short description | All your company email, operated by agents and reviewed by you. |
| Long description | Operate product, lifecycle, and marketing email with Banger: create Mailboxes, send Product email, run Journeys and Broadcasts, manage audiences, review Approvals, and inspect Logs through one governed MCP connection. Includes a skill that turns product and business context into a reviewable email growth plan. |
| Components | 1 MCP server (`banger`, remote HTTP, OAuth), 1 skill (`operate-company-email`) |
| Network endpoints | `https://api.bangermail.com` only (MCP, `/oauth/*`, `/.well-known/*`) |
| Credentials | None stored by the plugin; per-workspace OAuth grant issued at first use, revocable from the Banger app |
| Hooks / local execution | None |
| License | Proprietary (BangerMail Inc.); hosted service under https://bangermail.com/terms/ |
| Privacy policy | https://bangermail.com/privacy/ |
| Homepage | https://bangermail.com/banger-mcp/ |
| Support | hello@team.bangermail.com |
| Logo | `assets/banger-logo.png` (light), `assets/banger-logo-dark.png` (dark), `assets/banger-app-icon-128.png` (icon) |

Before submitting, from the public repo checkout:

```bash
claude plugin validate .
claude plugin validate .claude-plugin/plugin.json
```
