# Setup Notes
## CLAUDE.md choices
I included the essential commands (dev, test, lint) and the core architecture (server.js entry point, routes/ structure, db/store.js for data). I left out obvious things like file names that Claude can see, and any sensitive or one-off notes. Keeping it short means Claude actually reads it.

## Permission rules (in `.claude/settings.json`)
- `allow: npm test:*` — lets Claude run tests safely to verify changes
- `allow: npm run lint:*` — lets Claude check code style without a prompt
- `deny: Read(./.env)`, `Read(./.env.*)` — protects secrets (including `.env.local` etc.) from being read
- `deny: Bash(cat .env*)` — blocks the obvious shell route around the Read rule (pattern-based, so not airtight)
- `deny: git push --force:*`, `git push -f:*` — prevents accidental force pushes that could lose history
- `ask: git push:*` — forces confirmation before any push (deny rules take precedence, so force pushes stay blocked)

Without the deny rules, Claude could accidentally read .env (exposing API keys) or force-push and destroy commit history.

## Summary
I set up all three permission levels: allow, ask, and deny. NOTES.md documents why each permission rule exists. Because of the `ask` rule, Claude has to get my confirmation before it pushes any work.
