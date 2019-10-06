# Enemy Spawner

The goal is to have an object that represents an enemy plane spawner which will continuously spawn enemy planes

## Enemy Spawn Object

* Create a new object called "obj_enemy_spawner"

* Add a new script to the "Create" event and initialize a variable that will keep track of when it is time to spawn a new enemy. Call the variable "enemy_1_spawn_timer" and set it's value to 0.

* Add a new script to the "Step" event and write some code that does the following logic
  * Increases the "enemy_1_spawn_timer" value by 1. This means that once the value equals the room speed (set to 60 for our game) then 1 second will have passed.

  ```C#
  enemy_1_spawn_timer++
  ```

  * Spawn an enemy every 2 seconds by checking if "enemy_1_spawn_timer" is greater than two times the room speed.

```C#
// Is it time to spawn an enemy ?
if (enemy_1_spawn_timer > (2 * room_speed))
{
    // Yes, time to spawn an enemy !
    // All code for spawning the enemy goes in here
}    
```

  * Generates a random X value for the enemy plane from 0 to the width of the screen, remembering to subtract the width of the sprite from the room width so the plane does not appear off the side of the screen !
```C#
    spawn_x = random_range(0, room_width - sprite_get_width(spr_enemy_plane_1))
```

  * Set the Y value for the enemy to be 50 pixels off the screen so the plane doesn't look like it teleports in from nowhere
```C#
spawn_y = 0 - 50
```
  * Creates the enemy at the randomly generated point
```C#
    instance_create(spawn_x, spawn_y, obj_enemy_plane_1)
```
  * Resets the spawn time for enemy to 0 so another enemy can be generated
```C#
enemy_1_spawn_timer = 0
```

## Testing the Enemy Spawner
* In your test room called "room_test" delete all instances of the enemy planes that you have put in there
* Now place an instance of the "obj_enemy_spawner" object
* Start the game and see if the spawning of enemies is working
