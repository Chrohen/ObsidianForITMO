Casting is an action that takes an [[Actor]] of a specific class and tries to trear it as if it were a different class. Casting can succeed or fail. If casting cucceeds, you can then access class-specific functionality on the [[Actor]] you cast to.

For example, let's say you're making a game where you have multiple types of Volumes that can affect the player character in different ways. One of this volumes is Fire, which decreases player health over time. When the player overlaps with any Volume in the Level, you can cast that Volume to Fire to try to access its ""damage player health"" functionality.
- If the cast succeeds - that is, if the player is standing in the fire -> the player's health starts to decrease.
- If the cast fails - that is, if the player is standing in any other lind of Volume -> their health is not affected.

Casting is different from simply checking whether an Actor is of a given class, which would return a binary (yes or no) answer, but wouldn't allow you to interact with any specific functionality of that class.

---
#UnrealEngine