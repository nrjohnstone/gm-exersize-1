# Enemy Plane

The goal is to have an enemy plane object that can fly down the screen and collide with bullets

## Create the enemy plane sprite

* Create a sprite called "spr_enemy_plane_1" in Game Maker and load the sprite "plane_2_animated.png" from the resources folder
* The sprite is a sprite map so you will need to use the "Create from strip" menu item in Game Maker
  * The sheet is 189 pixels by 46 pixels and has a single row of 3 images. That means to find the width of each image you should divide 189 by 3.

![](/resources/plane_2_animated.png)

* Make sure the origin is set to 0,0
* Make sure the background color of white is set to transparent by using the menu option "Erase a color" in the sprite editor menu

## Create the enemy plane object

* Create a player object called "obj_enemy_plane_1" and assign the sprite from the previous step

## Add the enemy plane to the room

* Add an instance of the enemy plane object to the room near the top of the screen for testing.

## Making the enemy plane move

Since the sprite faces up the screen, but in GameMaker the angle 0 (or 360) for direction is facing right across the screen, to make sure we can have the enemy planes fly any angle across the screen we will need to adjust the image direction.

Increase the direction rotates the object to the left, as show in the picture below, while subtracting from the direction makes it rotate to the right.

![](/resources/directionmap.gif)

* Create a "Step" script for the enemy plane object "obj_enemy_plane_1"
* The object variable "image_direction" will rotate the sprite to face in any desired direction. The object variable "direction" contains the actual direction the object is facing.
* A direction value of 0 means the object is moving right across the screen, but since the sprite is facing up the screen we need to make sure we subtract an adjustment value when we set the image direction
* First in the "Step" script set the direction so the plane flys down the screen and the speed so the moves in the direction it is facing.
```C
direction = 270
speed = 5
```
* Then the code to add to the Step script to set the image direction is below, but you will need to figure out what the number to use for the ?
```C
image_direction = direction - ?
```

## Collision with bullets

We need to have the bullets check to see if they are colliding with the enemy plane.

* In the enemy plane object, add a script to the "Create" event and initialize a new variable called "is_dead" to false
```C
is_dead = false
```
* In the bullet object "Step" script "obj_player_bullet" add a section of code that checks for a collision with the enemy plane object "obj_enemy_plane_1"
* When there is a collision with an enemy plane object, we will set the "is_dead" variable inside the enemy plane to "true"
* The following functions will be useful
  *  `instance_place(x, y, object)` : This checks to see if there is an instance at x,y of the object
  * `instance_destroy()` : This will destroy the instance that is currently running the script
* The code for to put in the bullet Step script looks like this
```C
if (place_meeting(x, y, obj_enemy_plane_1))
{
    // Set a variable to the instance of the enemy plane we collided with
    enemy_plane = instance_place(x, y, obj_enemy_plane_1)
    // Tell the enemy plane it is dead by setting the "is_dead" variable
    enemy_plane.is_dead = true
    // Destroy this bullet instance
    instance_destroy()
}
```

## Enemy plane death

Now that the bullets are hitting the enemy plane and setting the "is_dead" variable to true, we need to make sure the enemy plane is destroyed !

* In the "Step" script for the enemy plane object "obj_enemy_plane_1" check the "is_dead" variable for true, and if it is then destroy yourself !
  * Remember to check if a variable is true you don't have to add "== true"
```C
// Check if this instance is dead
if (is_dead)
{
    instance_destroy()
}
```