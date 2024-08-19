Events are nodes that are called fromm gameplay cade to begin execution of an individual network within the **EventGraph**. they enable Blueprints to perform a series of actions in response to certain events that occur within the game, such as when the game stars, when level resets, or when a player takes damage.

Events can be accessed within Blueprints to implement new functionality or to override or augment functionality. Any number of **Events** can be used within a single **EventGraph**; though only one of each type may be used.

An event can only execute a single object. If you want to trigger multiple actions from one event, you will need to string them together linearly.

| ![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/874cd46d-df8c-4592-af16-feed833a6638/eventsexpanded.png) | ![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/db698dd0-2172-4c6e-854a-7b9b5e39d363/levelbpeventsexpanded.png) |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
## Event Level Reset
*This Blueprint Event node is only available in the Level Blueprint*
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/410195dc-e8c3-4ae1-b059-0abf6b9365a3/levelreset.png)
The **Level Reset** event sends out an execution signal when the level restarts. This is useful when you need something to be triggered once a level has reloaded, such as in a gaming situation when the player has died but the level does not need to reload.
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/95f7fc37-190e-4d04-a3ca-37da128d3e0f/levelreset_example.png)

## Event Actor Begin Overlap
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/75e3d042-06bd-4779-95a2-61cb0c5dda74/beginoverlap.png)
This event will execute when a number of conditions are met at the same time:
- Collision response between the actors must allow Overlaps
- Both [Actors](Actor.md) that are to execute the event have **Generate Overlap Events** set to true.
- And finally, both [Actors'](Actor.md) collision starts ovelapping; moving together or one is created overlapping the other.

For more information on collision, see: [Collision Responses](https://dev.epicgames.com/documentation/en-us/unreal-engine/collision-in-unreal-engine)

![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/feb18256-7eec-4c50-992f-7b5122c1b415/beginoverlapex.png)
*When this Blueprint Actor overlaps the Actor stored in the Player Actor variable, it will increment the Counter integer variable*

| Item        | Description                                                   |
| ----------- | ------------------------------------------------------------- |
| Output Pins |                                                               |
| Other Actor | Actor - This is the Actor that is overlapping this Blueprint. |

## Event Actor End Overlap
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/16f53eb2-ed8e-41cf-949e-1acb8d1007cd/endoverlap.png)
This event will execute when a number of conditions are met at the same time:
- Collision response between the actors must allow Overlaps.
- Both [Actors](Actor.md) that are to execute the event have **Generate Overlap Events** set to true.
- And finaly, both [Actors'](Actor.md) collision stop overlapping; moving appart or if one is destroyed.

For more information on collision, see: [Collision Responses](https://dev.epicgames.com/documentation/en-us/unreal-engine/collision-in-unreal-engine)

![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/5db7ed22-38e3-4a65-a602-39c9ca8714ae/endoverlapex.png)
*When this Blueprint Actor stops overlapping any other Actor except the Actor stored in the Playe Actor variable, it will destroy the Actor that overlapped it*

| Item        | Description                                                   |
| ----------- | ------------------------------------------------------------- |
| Output Pins |                                                               |
| Other Actor | Actor - This is the Actor that is overlapping this Blueprint. |
## Event Hit
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/47882152-f40c-4795-9b2b-6d17369fccbe/eventhit.png)
This event will execute as long as the collision settings on one of the [Actors](Actor.md) involved have **Simulation Generates Hit Events** set to true.

*If you are creating movement using Sweeps, you get this event even if you don't have the flag selected. This occurs as long as the Sweep stops you from moving past blocking object.*

| Item           | Type               | Description                                                                                                                                                                                                      |
| -------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Output pins    |                    |                                                                                                                                                                                                                  |
| My Comp        | PrimitiveComponent | The component on the executing [[Actor]] tha was hit.                                                                                                                                                            |
| Other          | [[Actor]]          | The other [[Actor]] involved in the collision.                                                                                                                                                                   |
| Other Comp     | PrimitiveComponent | The component on the [[Actor]] involved in the collision that was hit.                                                                                                                                           |
| Self Moved     | Boolean            | Used when receiving a hit from another object's movement (if false), the directionns if **Hit Normal** and **Hit Impact Normal** will be adjusted to indicate from the other object agains the object being hit. |
| Hit Location   | Vector             | The location of contact between the two colliding [Actors](Actor.md)                                                                                                                                             |
| Hit Normal     | Vector             | The direction of the collision                                                                                                                                                                                   |
| Normal Impulse | Vector             | The force that te [Actors](Actor.md) collided with                                                                                                                                                               |
| Hit            | Struct HitResult   | All the data collected in a Hit, you can pull off and "break" this result to gain access to the individual bits of data.                                                                                         |

![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/50aa29cd-cda9-4b90-b064-2aa7f761f1d3/eventhitex.png)
*In this example, when this Blueprint executes Hit it will spawn an explosion effect at the poin of impact*
## Event Any Damage
This Blueprint Event node executes only on the server. For single player games, the local client is considered the server.
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/7b2adbdf-009f-45a8-8f32-5d9dd0cbf4f3/anydamage.png)
This event is passed along when general damage is to be dealt. Like drowning or enviromental damage, not specifically point damage or radial damage.

| Item          | Type              | Description                                                                                                                                                                                     |     |
| ------------- | ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| Output pins   |                   |                                                                                                                                                                                                 |     |
| Damage        | Float             | The amount of damage being passed into the [[Actor]]                                                                                                                                            |     |
| Damage Type   | Object DamageType | This is the object that contains additional dta on the Damage being dealt                                                                                                                       |     |
| Instigated By | Controller        | The Controller of the [[Object]] that is responsible for the damage. This could be the [[Player Controller]] that fired a gun or an [[AIController]] that threw the grenade to deal the damage. |     |
| Damage Causer | [[Actor]]         | The [[Actor]] that caused the damage. This would be like a bullet or explosion                                                                                                                  |     |
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/2367e1ba-a99e-4501-ae91-8caae4db75d8/anydamageex.png)
*Here if the damage being dealt to the Actor is coming from Water, it will subtract health and print a warning to the screen*
## Event Point Damage
This Blueprint Event node executes only on the server. For single player, the local client is considered the server.
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/6777277b-a75f-4d17-8d16-18ecc90d1cfb/pointdamage.png)
**Point Damage** is meant to represent damage dealt by projectiles, hit scan weapons, or even melle weaponry.

| Output Pin          | Type               | Description                                                                                                                             |
| ------------------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| Damage              | Float              | The amount of damage being passed into the [[Actor]].                                                                                   |
| Damage Type         | Object DamageType  | This is the object that contaims additional data on the Damage being dealt.                                                             |
| Hit Location        | Vector             | The location of where the damage is being applied.                                                                                      |
| Hit Normal          | Vector             | The direction of the collision.                                                                                                         |
| Hit Component       | PrimitivrComponent | The Component on the executing [[Actor]] that was hit.                                                                                  |
| Bone Name           | Name               | The name of the bone that was hit.                                                                                                      |
| Shot from Direction | Vector             | The direction the damage came from.                                                                                                     |
| Instigated By       | [[Actor]]          | The [[Actor]] that is responsible for the damage. This would be the [[Actor]] that fired a gun or threw the grenade to deal the damage. |
| Damage Causer       | [[Actor]]          | The [[Actor]] that caused damage. This would be like a bullet or explosion.                                                             |

![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/4296b556-0bc1-4c1e-b65b-be6765832a27/pointdamageex.png)
*In this example, when any damage is received, the damage dealt is subtracted from the Actor's health, but if the Head of the Actir us hit, then the Actor's health is set to -1.*
## Event Radial Damage
This Blueprint Event node executes only on the server. For single player games, the local client is considered the server.
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/d8d16e7e-9bc0-447f-8050-e4b178487ea4/radialdamage.png)
The **Radial Damage Event** is called whenever tthe parent [[Actor]] for this sequence recevies radial damage. This is useful for handling events based on explosion damage caused indirectly.

| Output Pin      | Type              | Description                                                                                                               |
| --------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Damage Received | Float             | The amount of damage received from the event.                                                                             |
| Damage Type     | Object DamageType | This is the object that contaims additional data on the Damage being dealt.                                               |
| Origin          | Vector            | This gives the location in 3D space where the damage originated.                                                          |
| Hit Info        | Struct HitResult  | All the data collected in a Hit, you can pull off and "break" this resault to gain access to the individual bits of data. |
| Instigated By   | Controller        | The Controller (AI or Player) that instigated the damage.                                                                 |
| Damage Causer   | [[Actor]]         | The [[Actor]] that caused damage. This would be like a bullet or explosion.                                               |

![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/84817f0b-9f1b-420d-8a52-2c052e90f22b/radialdamageex.png)
## Event Actor Begin Cursor Over
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/4e08fb37-34a4-4860-af06-ebf703c28228/begincursorover.png)
When using the mouse interface, when the mouse is moved over an [[Actor]], this event will execute.
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/0b4703a5-8769-4560-b427-f264f3c0ffc4/begincursoroverex.png)
*Once the mouse passes over this Actor it sets the scalar Parameter named Highlight on the Dynamic Material Instance to 1.0*
## Event Actor End Cursor Over
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/fd430bf0-90e6-4756-ac3c-c439599050d8/endcursorover.png)
When using the mouse interface, when the mouse cursor is moved off an [[Actor]], this event will execute.
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/f1c38877-9c63-4fe8-bcd1-07a53886ee08/endcursoroverex.png)
*This will set the Actor stored in Target Notification to hidden in game*
## Event Begin Play
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/cf06dff5-daa4-4e1e-b45a-bd618b40b9cd/beginplay.png)
This event is triggered for all [Actors](Actor.md) when the game is started, any [Actors](Actor.md) spawned after the game is started will have this called imidiately.
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/9f2ca478-b678-410e-b867-de8ffba46cf2/beginplayex.png)
*When beginning play, this Actor will set Health to 1000 and Score to 0.*
## Event End Play
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/245a3cff-3ca1-41ca-91c2-2fca3772953e/endplay.png)
This event is executed when the [[Actor]] ceases to be in the World.
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/0b6561b5-fb9b-4860-b077-f0c22c4b1019/endplayex.png)
*Once this Actor is no longer in the World, a String will output to indicate the reason for the Event being called*

| Output Pins     | Type                | Description                                                              |
| --------------- | ------------------- | --------------------------------------------------------------------- |
| End Play Reason | enum EEndPlayRe An enum indicating the reason for why Event End Play is being called. y  t  n  |

## Event Destroyed
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/6dc1e180-46da-4d44-811a-dfa11c848158/destroyed.png)
This event is executed when the [[Actor]] is Destroyed.
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/efa072b9-d939-49ed-a482-609735e8f4f1/destroyedex.png)
*In this example, the variable of Score is being set to Value plus Score*

***The Destroyed Event will be deprecated in a future release! The functionality of the Destroyed function has been incorporated into the EndPlay function***

## Event Tick
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/70afcdd3-b241-47bd-bb8e-48e61148593c/tick.png)
This is  a simple event that is called on every frame of gameplay.

| Output Pins   | Type  | Description                                    |
| ------------- | ----- | ---------------------------------------------- |
| Delta Seconds | Float | This outputs the amount of time between frames |
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/1723573a-3c24-4991-8660-875d944ae17c/tickex.png)
*This example  uses Delta Seconds to form a count down timer that displays in the log with the final tick being "Blast Off!"*

## Event Receive Draw HUD
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/8a4bfd81-453b-433f-9fa6-fc0191a50003/drawhud.png)
This is a specialized event that enables Blueprints to draw to the HUD. The HUD draw nodes require this event to be the one that creates them.

| Output Pins | Type | Description                                |
| ----------- | ---- | ------------------------------------------ |
| Size X      | Int  | The width of the render window in pixels.  |
| Size Y      | Int  | The height of the render window in pixels. |

![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/6d2600d5-c8a1-4654-a556-3ec13c6d2f10/drawhudex.png)
*This will create a clickable Hit Box in the center of the render window, with a red box behind it so you can see it*
## Custom Event
![](https://d1iv7db44yhgxn.cloudfront.net/documentation/images/2f7424d0-7325-4e43-add1-de934a57eeff/name_custom_event.png)
The Custom Event node is a specialized node with its own workflow.

To learn more:
- [Custom Events](https://dev.epicgames.com/documentation/en-us/unreal-engine/custom-events-in-unreal-engine): Create your own events that can be called at any point in your Blueprint's sequence.
- [Calling Events through Sequencer](https://dev.epicgames.com/documentation/en-us/unreal-engine/fire-blueprint-events-during-cinematics-in-unreal-engine): Create events to be triggered at specific times during the playback of a cinematic sequence.

---
Links:
- [Events](https://dev.epicgames.com/documentation/en-us/unreal-engine/events-in-unreal-engine) 
---
#UnrealEngine 