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
* The code to add to the Step script to set the image direction is here, but you will need to figure out what the number to use for the ?
```
image_direction = direction - ?
```
* Also set the direction so the plane flys down the screen and the speed so the moves in the direction it is facing
```
direction = 270
speed = 5
```
