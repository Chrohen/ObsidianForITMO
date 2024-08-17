A **Player State** is the state of a participant in the game, such as human player or a bot that is simulating a player. Non-player AI that exists as part of the game doesn't have a Player State.

Some examples of player information that the Player State can containe include:
- Name
- Current level
- Health
- Score
- Whether they are currently carrying the flag in a Capture the Flag game

For multiplayer games, Player States for all players exist on all machines and can replicate data from server to the client to keep things in sync.
This different from a [[Player Controller]], which will only exist on the machine of the player it represents.

The asossiate C++ class is **`PlayerState`**.

---
Links:
- [Gameplay Framework Quick Reference](https://dev.epicgames.com/documentation/en-us/unreal-engine/gameplay-framework-quick-reference-in-unreal-engine)
---
#UnrealEngine