Blueprints are special assets that provide an intuitive, node-based intarface that can be used to create new types of [Actors](Actor.md) and script level events; giving designers and gameplay programmers the tools to quickly create and iterate gameplay from within Unreal Editor without ever needing to wright a line of code.

| Blueprints (UE5)         | C++(UE5)                 |
| ------------------------ | ------------------------ |
| Blueprint Asset          | .h/.cpp files            |
| UBlueprintGeneratedClass | UClass                   |
| ParrentClass             | :\[ClassName]            |
| Variable                 | UProperty()              |
| Graphs/Events            | UFunction()              |
| Class Defaults           | native cunstructor       |
| Components List          | native cunstructor       |
## Types of Blueprints

Bluprints can be one of several types that each have their own specific use from creating new types to scripting level events to defining interfaces or macros to be used by other Blueprints.

### Blueprint Class

A **Blueprint class**, often shortened as **Blueprint**, is an asset that allows content to easily add functionality on top of existing gameplay classes. Blueprints are created inside if Unreal Editor visually, instead of typing code, and saved as assets in a content package. These essentially define
a new class or type of [[Actor]] which can then be placed into maps as instances that behave like any other type of [[Actor]].

### [[Data-Only Blueprint]]

A **Data-Only** Blueprint is Blueprint Class that contains only the code (in the form of node graphs), variablesm and components inherited from its parent. These allow inhereted properties to be tweaked and modefied, but no new elments can be added. These are essentially a replacement for archetypes and can be used to allow designers to tweak properties or set items with variations.
### [[Level Blueprint]]

A **Level Blueprint** is a specialized type of Blueprint that acts as a level-wide global event graph. Each level in project has its own Level Blueprint created by default that can be edited within the Unreal Editor, however new Level Blueprint cannot be created throgh the editor interface.
### [[Blueprint Interface]]

A **Blueprint Interface** is a collection of one or more functions - name only, no implementation - that can be added to other Blueprints. Any Blueprint that has Interface added is guaranted to have those functions. The functions of the Interface can be given functionality in each of the Blueprints that added it. This is essentially like concept of [interface](Interface.md) in general programming, which allows multiple different types of [Objects](Object.md) to all share and be accessed through comon interface.
### [[Blueprint Macro Library]]

A **Blueprint Macro Library** is a container that holds a collection of **Macros** or self-contained graphs that can be placed as nodes in other Blueprints. These can be time-savers as they can stor commonly used sequences of nodes complete with inputs and outputs for both execution and data transfer.
### Blueprint Utilites

A **Blueprint Utilites** (or **Blutility** for short), is an editor-only Blueprint that can be used to perform editor actions or extend editor functionality. These can expose [[Events]] with no parameters as buttons in the UI and have the ability to execute any functions exposed to *Blueprints* and act on the current set of selected [Actors](Actor.md) in the viewport.

----
Links:
- [Blueprints Visual Scripting](https://dev.epicgames.com/documentation/en-us/unreal-engine/blueprints-visual-scripting-in-unreal-engine) 
- [Blueprint Visual Overview](https://dev.epicgames.com/documentation/en-us/unreal-engine/overview-of-blueprints-visual-scripting-in-unreal-engine)
- [Basic Scripting with Blueprints](https://dev.epicgames.com/documentation/en-us/unreal-engine/basic-scripting-with-blueprints-in-unreal-engine)
---
#UnrealEngine #Blueprints #BassicAssets


%% Also must read/write about Blueprint Anatomy%%