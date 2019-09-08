# Goal

To have a test room with a player object that can move around the screen when up/down/left/right keys are pressed.
The player object should also not be able to move any part of the sprite offscreen.

## Create the player sprite

* Create a sprite "spr_player" in Game Maker and Use the "player_plane.png" sprite from the resources folder

![GitHub Logo](/resources/player_plane.png)

* Make sure the origin is set to 0,0
* Make sure the background color of white is set to transparent

## Create the player object

* Create a player object called "obj_player" and assign the sprite from the previous step

## Create the test room

* Create the test room called "room_test"
* Set the speed of the room to 60
* Add the player object to the middle of the room near the bottom

## Create the player initialize script

* Create a blank script for the "Step" event
* Add code to make the player respond to the left arrow key
  * You will need to use the `keyboard_check()` function to always move while the key is held down
* Add code to make the player respond to the right arrow key
* Add code to make the player respond to the up arrow key
* Add code to make the player respond to the down arrow key
* Add code to stop the player from moving off the screen in any direction
  * You will need to use the following variables for the checks
    * `room_width`, `room_height`, `sprite_width` and `sprite_height`



