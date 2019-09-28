# Shooting

The goal is to end up with the player able to shoot bullets when the space key is pressed

## Create the bullet sprite

* Create a sprite called "spr_player_bullet" in Game Maker and load the sprite "player_bullet.png" from the resources folder

![](/resources/player_bullet.png)

* Make sure the origin is set to 0,0

## Create the bullet object

* Create an object called "obj_player_bullet" in Game Maker

## Fire the bullet when space is pressed

* In the existing script of the "Step" event for the obj_player add a check for when the spacebar is pressed and if it is then
  * Create an instance of the "obj_player_bullet"
  * Set the direction to point up the screen
  * Set the speed of the bullet to 12

*example code for creating an instance of the player bullet and setting the direction and speed*
```
if (keyboard_check_pressed(vk_space))
{
    bullet = instance_create(x, y, obj_player_bullet)
    bullet.direction = 90
    bullet.speed = 12  
}
```

## Make sure the bullets destroy themselves when off screen

Even when an instance is offscreen it is still taking up memory and cpu, so unless we destroy all of the bullet instances then the game will eventually run slower and slower.

* In the object for the player bullet "obj_player_bullet" add a new script for the Step event
* Check if the y position of the bullet has moved offscreen, and if it has then destroy the instance
  * HINT: Use `instance_destroy()` in a script to have an instance destroy itself

```
if (y < 0)
{
    instance_destroy()
}
```
