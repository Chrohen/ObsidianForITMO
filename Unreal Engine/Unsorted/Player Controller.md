A **Player Controller** takes player input and translates it into interactions in tthe game. Every game has at least one Player Controller in it. A Player Controller often possesses a [[Pawn]] or [[Character]] as a a representation of the player in a game.

The **Player Controller** is also the primary network interaction point for multiplayer games. During multiplauer play, the server has one instance of Player Controller for every player in the game since it must be able to make network function calls to each player, each client only has the Player Controller that corresponds to their player and can only use their Player Controller to communicate with the server.

The associated C++ class is `PlayerController`.

----
Links:
- [Player Controllers](https://dev.epicgames.com/documentation/en-us/unreal-engine/player-controllers-in-unreal-engine)
---
#UnrealEngine


