# .claude

Personal Claude Code configuration — synced across machines.

## What's tracked

- `commands/` — custom slash commands
- `plugins/` — plugin marketplace config
- `settings.json` — user preferences

## Setting up on a new machine

> **Important:** `.credentials.json` is excluded from this repo. After cloning, you'll need to run `claude` once to authenticate and regenerate it.

```bash
# 1. Back up any existing config
mv ~/.claude ~/.claude.bak

# 2. Clone this repo in its place
git clone git@github.com:YOUR_USERNAME/.claude.git ~/.claude
```
