https://docs.unity3d.com/ScriptReference/CharacterController.html

- *Character movement*
- *Collision detection
- *Uneven ground
- *Slopes
- *Stairs


	***You cant rotate Y axis*
	

### Properties

|                                                                                                                  |                                                                                                                                                                                                                                                                                                   |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [center](https://docs.unity3d.com/ScriptReference/CharacterController-center.html)                               | The center of the character's capsule relative to the transform's position.                                                                                                                                                                                                                       |
| [collisionFlags](https://docs.unity3d.com/ScriptReference/CharacterController-collisionFlags.html)               | What part of the capsule collided with the environment during the last CharacterController.Move call.<br>.Above<br>.Sides<br>.Below<br>Вызывается детект колизии на основе последнего движения самого персонажа, то есть его перемещения должны влиять на детект колизии.<br>                     |
| [detectCollisions](https://docs.unity3d.com/ScriptReference/CharacterController-detectCollisions.html)           | Determines whether other rigidbodies or character controllers collide with this character controller (by default this is always enabled).<br>(Если выключено и персонаж двигается то обьекты будут влиять так , что он просто переступает,  если не двигается то ригидбади пройдет просто сквозь) |
| [enableOverlapRecovery](https://docs.unity3d.com/ScriptReference/CharacterController-enableOverlapRecovery.html) | Enables or disables overlap recovery. Enables or disables overlap recovery. Used to depenetrate character controllers from static objects when an overlap is detected.<br>(Выталкивание из статических коллайдеров)                                                                               |
| [height](https://docs.unity3d.com/ScriptReference/CharacterController-height.html)                               | The height of the character's capsule.                                                                                                                                                                                                                                                            |
| [isGrounded](https://docs.unity3d.com/ScriptReference/CharacterController-isGrounded.html)                       | Was the CharacterController touching the ground during the last move?                                                                                                                                                                                                                             |
| [minMoveDistance](https://docs.unity3d.com/ScriptReference/CharacterController-minMoveDistance.html)             | Gets or sets the minimum move distance of the character controller.<br>(Smallest change in distance for character to move)<br>(Нулевое или очень минимальное для адекватного торможения)                                                                                                          |
| [radius](https://docs.unity3d.com/ScriptReference/CharacterController-radius.html)                               | The radius of the character's capsule.                                                                                                                                                                                                                                                            |
| [skinWidth](https://docs.unity3d.com/ScriptReference/CharacterController-skinWidth.html)                         | The character's collision skin width.<br>(10 процентов больше от коллайдера рекомендовано)                                                                                                                                                                                                        |
| [slopeLimit](https://docs.unity3d.com/ScriptReference/CharacterController-slopeLimit.html)                       | The character controllers slope limit in degrees.                                                                                                                                                                                                                                                 |
| [stepOffset](https://docs.unity3d.com/ScriptReference/CharacterController-stepOffset.html)                       | The character controllers step offset in meters.                                                                                                                                                                                                                                                  |
| [velocity](https://docs.unity3d.com/ScriptReference/CharacterController-velocity.html)                           | The current relative velocity of the Character (see notes).<br>(Появляется только на основе методов Move и SimpleMove)                                                                                                                                                                            |

### Public Methods

|                                                                                            |                                                                                                               |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------- |
| [Move](https://docs.unity3d.com/ScriptReference/CharacterController.Move.html)             | Supplies the movement of a GameObject with an attached CharacterController component.                         |
| [SimpleMove](https://docs.unity3d.com/ScriptReference/CharacterController.SimpleMove.html) | Moves the character with speed.                                                                               |
|                                                                                            | (Или в фикседАпдейт віполняется или на дельтаТайм умножается, +возможно автоматически гравитацию расчитывает) |

### Messages

|                                                                                                                      |                                                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| [OnControllerColliderHit](https://docs.unity3d.com/ScriptReference/CharacterController.OnControllerColliderHit.html) | OnControllerColliderHit is called when the controller hits a collider while performing a Move.<br>(Когда персонаж двигается сам и коллайдится) |