A **Blueprint Macro Library** is a container that holds a collection of **Macros** or self-contained graphs that can be placed as nodes in other Blueprints. These can be time-savers as they can stor commonly used sequences of nodes complete with inputs and outputs for both execution and data transfer.

Macros are shared among all graphs that reference them, but they are auto-expanded into graphs as if they were collapsed node during compiling. This means that Blueprint Macro Libraries do not need to be compiled. However, changes to Macro are only reflected in graphs that reference that Macro when th Blueprint containing those graphes is recompiled.

---
Links:
- [Macro Library](https://dev.epicgames.com/documentation/en-us/unreal-engine/blueprint-macro-library-in-unreal-engine)
- [Making Macros](https://dev.epicgames.com/documentation/en-us/unreal-engine/making-macros-in-unreal-engine)
---
#UnrealEngine #Blueprints