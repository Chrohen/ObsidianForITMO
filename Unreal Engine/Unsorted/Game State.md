A **Game State** is a container that holds information you want replicated to every client in a game. In simpler terms, it is 'The State of the Game' for every one connected.

Some examples of what the Game State can contain include:
- Information about the game score
- Whether a match has started or not
- How many AI characters to spawn based on the number of players in the world

For multiplayer games, there is one local instance of the Game State on each player's machine. Local Game State instances get their updated information from the server's instance of the Game State.

The assossiated C++ class is **`GameState`**.

---
Links:
- [Game Mode and Game State](https://dev.epicgames.com/documentation/en-us/unreal-engine/game-mode-and-game-state-in-unreal-engine)
---
#UnrealEngine