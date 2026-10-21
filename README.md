# cod2-map-maker agent (Claude Code)

A Claude Code subagent for building Call of Duty 2 single-player maps: geometry generation,
compiling (cod2map / cod2rad / connectpaths), AI path audits, GSC scripting, vehicles, mortar
crews, squads, objectives and playtest bug-fixing.

Pairs with the skill repo: **https://github.com/X1NPAR1/cod2-map-maker-skill** (recommended: install both).

## Install
```bash
git clone https://github.com/X1NPAR1/cod2-map-maker-agent
mkdir -p ~/.claude/agents
cp cod2-map-maker-agent/agents/cod2-map-maker.md ~/.claude/agents/
```
Windows: copy it to `%USERPROFILE%\.claude\agents\`.

## Use
Ask Claude Code: *"Use the cod2-map-maker agent to build a winter outpost assault map in
F:\Games\Call of Duty 2"*, or run `/agents` and pick it.

## Requirements
- Call of Duty 2 (patch 1.3) and the CoD2 Mod Tools installed into the game folder.
- Python 3 for generators and audits.

## Credits
The rules come from building and playtesting several full campaign maps. Every rule was measured in game.
