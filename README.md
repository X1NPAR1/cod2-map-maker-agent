# cod2-map-maker — Claude Code agent for Call of Duty 2 single-player maps

A Claude Code subagent that **builds, tests and ships complete Call of Duty 2 single-player missions**. It plans the map with you and generates the geometry. It compiles the map, audits the AI path network and writes the GSC mission script. It then tours the map with screenshots and plays the whole mission with an auto-player before handing it to you for a playtest.

> **Built with this agent:** [cod2-maps](https://github.com/X1NPAR1/cod2-maps), a five-mission campaign of about 45 minutes to 1 hour with a one-click installer.
>
> Knowledge base: [cod2-map-maker-skill](https://github.com/X1NPAR1/cod2-map-maker-skill). Install both; the agent follows the skill's rules and references.

---

## How it works

| Phase | What the agent does | Gate |
|---|---|---|
| **Plan** | Interviews you in plan mode about the setting, layout, squad, enemies, vehicles, events and audio | You approve the plan |
| **Build** | Generates the terrain, roads, sky box and border ridges in Python. Buildings, walls and set dressing are stock prefabs of the map's nation (US/Normandy, British desert, German), placed the way Infinity Ward did in newvillers | Generator assertions, stock-quality numbers |
| **Compile** | Runs cod2map, cod2rad and `g_connectpaths`, then decodes the AI path network | LEAK 0, no unreachable areas |
| **Script** | Writes the mission: objectives, squad brain, waves, vehicles, scenes, sound and strings | 0 script errors, 0 unknown aliases |
| **Visual QA** | Takes a screenshot tour with game sound off and fixes what it sees | Nothing floating, no visible sky box edge |
| **Flow test** | An auto-player plays the full mission and logs every phase | Reaches the end, 0 runtime errors |
| **Playtest** | Launches the game for you and fixes every item on your list | Your approval |
| **Ship** | Updates the skill and agent with what it learned; publishes the map on your go-ahead | — |

## Install

```bash
git clone https://github.com/X1NPAR1/cod2-map-maker-agent
mkdir -p ~/.claude/agents
cp cod2-map-maker-agent/agents/cod2-map-maker.md ~/.claude/agents/
```

On Windows, copy the file to `%USERPROFILE%\.claude\agents\`.

## Use

Ask Claude Code something like:

> *Use the cod2-map-maker agent to build a winter outpost assault map in F:\Games\Call of Duty 2*

You can also run `/agents` and pick it.

## Stock reference maps

If you want a map "like" a stock level (newvillers, eldaba, matmata, toujane, decoytrenches...),
the agent first asks which parts you mean:
- the layout as a blueprint;
- specific areas (it decompiles the stock `.d3dbsp` and cuts them into prefabs);
- only the mood (fog, light, ambience, backdrops).

It then builds the map from those pieces.

## Principles

- **Measure, don't assume.** Compile logs, path audits, screenshots and flow-test logs come before any claim.
- **Use only stock assets and animations.** It uses the game's own models, sounds and cinematic animations. For example, it reuses the beltot truck scene for a truck finale.
- **The player never sees the seams.** No visible sky box edges, no spawning or teleporting in view, no floating props.
- **Your list is the next iteration.** Every playtest item gets fixed and verified again.
- **Nothing outward-facing without asking.** It only pushes, publishes or shuts the machine down when you say so.

## Requirements

- Call of Duty 2 with patch 1.3, and the CoD2 Mod Tools installed into the game folder.
- Python 3 and Windows PowerShell.

## Disclaimer

Fan-made and unofficial. Call of Duty is a trademark of Activision. No game assets are included.
