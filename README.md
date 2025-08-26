# Unity Bomberman - A 2D Arena Battle Game

This is a local multiplayer Bomberman-style game developed in the Unity Engine with C#. I created it as a final project for a high school computer science course.

## Gameplay & Features

This project is a complete gameplay loop, featuring:

* **Local Multiplayer:** Supports 2-4 players on a single keyboard, each with their own control scheme.
* **Core Bomb Mechanics:** Players can drop bombs that explode in four directions after a set timer.
* **Dynamic Explosions:** Explosions travel in a line until they collide with a wall, destructible obstacle, or another player, creating strategic depth.
* **Power-Ups:** Collectible items that enhance player abilities (e.g., extra bombs, increased explosion range).
* **Complete Game Flow:** Includes a main menu/homescreen, a score tracker during gameplay, and an end screen to declare the winner.
* **Audio Integration:** Background music and sound effects for a more immersive experience.

<!-- ## Screenshots

*(A gameplay GIF is highly recommended here to quickly show the core mechanics in action.)* 

<p align="center">
  <img src=".github/assets/bomberman-menu.png" alt="Main Menu" width="48%" />
  <img src=".github/assets/bomberman-gameplay.png" alt="Gameplay Screenshot" width="48%" />
</p> -->

## Technical Implementation

This project was built from the ground up in Unity focusing on creating maintainable code through OOP in C#.

* **Engine:** Unity Engine (2D Renderer)
* **Language:** C#

### Key C# Scripts & Systems:

* **Player and Movement Systems (`MovementController.cs`, `AnimatedSpriteRenderer.cs`):**
    * The **`MovementController.cs`** script is the brain behind player actions. It handles multi-player input from a single keyboard and translates it into movement. To achieve smooth, physics-based motion, it directly interfaces with Unity's physics engine by applying forces to the player's **`Rigidbody2D`** component.
    * The **`AnimatedSpriteRenderer.cs`** script works in tandem with the movement controller to manage the visual state of the character. It dynamically changes the character's sprites based on their movement direction and state (e.g., idle, walking up/down/left/right), providing clear visual feedback.
 
* **Bomb Placement and Explosion Logic (`BombController.cs` & **`bombPrefab`**):**
    * The system is split into two parts. The **`BombController.cs`**, attached to the player, handles the *placing* of bombs. It manages the number of bombs a player can have on screen at once and uses a C# coroutine to create a non-blocking fuse timer. This allows the game to continue running smoothly while a bomb is waiting to explode.
    * The **`bombPrefab`** contains the separate logic for the explosion itself. When the fuse timer from `BombController.cs` finishes, the bomb object is destroyed, triggering an explosion sequence. This sequence spawns explosion objects in four cardinal directions, which travel outwards until they collide with a solid object like a wall or another player, determined by Unity's collision system.

* **Object-Oriented Design:**
    * The code follows OOP principles, with each script acting as a self-contained component with a specific responsibility (e.g., movement, bomb logic). This component-based design, central to Unity development, allows for easy debugging, modification, and extension of features.

