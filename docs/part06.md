# Player Death

The goal is to have the player die when they collide with an enemy

## Add a new Script to the Player Object

* Add a new script for all of the collision checking to the "Step" event of the "obj_player". Add a triple forward slash comment to the top of the script to show that this is where the collison detection is happening
```C#
/// Collision checks
```
* The first thing to check is that the current x,y position of the "obj_player" is colliding with an instance of "obj_enemy_plane_1". If it is then we will put all the collision logic within this block.

```C#
if (place_meeting(x, y, obj_enemy_plane_1))
{
  // All collision code with enemy plane 1 goes in here
}
```

* We need to be able to tell the enemy plane that it is now dead after colliding with us, so the first thing to do is get a reference to the instance so we can set the "is_dead" variable

```C#
    instance = instance_place(x, y, obj_enemy_plane_1)    
```

* Now that we have the variable "instance" set to the enemy plane we are colliding with, we can set the "is_dead" variable to true

```C#
  instance.is_dead = true
```

* And the last thing to do is to destroy the player himself, for this we need to give the "obj_player" an is_dead variable as well. Open the script for the "Create" event of "obj_player" and create a new variable "is_dead" and set it to false
```C#
  is_dead = false
```

* Go back to the collision detection script in the "Step" event for "obj_player" and set is_dead to true for the player as well
```C#
  // Set the player to dead
  is_dead = true
```

* Add a new script to the "Step" event for "obj_player" and set the comment at the top to "player death"
```C#
/// Player Death
```

* In the Player Death script, check if the player is dead and end the game if they are
```C#
if (is_dead)
{
    instance_destroy()
    game_end()
}
```

* We will add explosions in the next part and then players lives after that