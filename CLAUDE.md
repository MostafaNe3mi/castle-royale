# Castle Royale — Project Brief

## What this is
A learning project, NOT a game-dev project. Two students (beginners in RL / neural networks) are using a simple 2D game to learn reinforcement learning. Keep the game design as simple as possible.

**Working style:** Claude writes the code; we learn the concepts as we go and do the debugging. Explain the RL/NN ideas behind what you write, briefly and clearly.

**Hardware:** main PC = Intel i7 12th gen + RTX 3070. Second machine (laptop) = i7 11th gen + MX450.

## The game (prototype rules)
- **World:** simple 2D map, visually rendered with a sprite per agent (not text-only).
- **Goal:** hold territory — a flag/strong point inside a castle in the middle of the map.
- **Agents:** 10 agents, free-for-all. They spawn equally spaced in 5 pairs (2 agents near each other).
- **Weapons:** everyone starts with a base weapon. Between each pair sits one upgraded weapon; only one of the two can take it (auto-pickup by walking onto it), and they keep it after respawning.
- **Castle:** the flag has 4 entrances, 3 are dead ends. For the prototype the real entrance is fixed.
- **Scoring:** only the agent currently holding the flag scores points over time. When the holder is eliminated, the flag opens and the next agent to reach and occupy it starts scoring.
- **Match end:** first to 200 points wins, or a 6-minute time limit → highest score wins (tie = no winner).

## Actions
- Move in 4 directions (up/down/left/right).
- Ranged weapons with limited range; facing-based shooting (agent can only shoot in the direction it faces).
- One-hit eliminations.

## Vision
- Fixed field of view that moves with the agent (prototype).
- At spawn, each agent can see its pair-mate (so they can contest the upgraded weapon).
- Later upgrade: reveal-as-you-go vision (walked areas stay visible).

## Death / anti-farming
- Respawn at own spawn point after a short delay, with brief spawn protection.
- Agents that die more often get extra seconds added to their respawn delay each death.
- No score for kills. Any future kill reward would only be for eliminating the flag holder.

## Rewards
- Reward for moving in the right direction (toward the objective) + flag-holding points.
- Reward system is NOT fixed up front — we'll tune it early based on what the agents actually do.

## Build plan (staged)
1. Small map with the flag and **one agent** ← start here
2. Two agents with one upgraded weapon
3. Full 10 agents, 4 entrances, flag scoring
4. Upgrades: reveal-as-you-go vision, randomized real entrance, tuned rewards
