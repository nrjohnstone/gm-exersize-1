# Make a moving player object

To have a test room with a player object that can move around the screen when up/down/left/right keys are pressed.

The player object should also not be able to move any part of the sprite offscreen.

## Create the player sprite

* Create a sprite "spr_player" in Game Maker and Use the "player_plane.png" sprite from the resources folder
* The sprite is a sprite map so you will need to use the "Create from strip" menu item in Game Maker
  * The sheet is 183 pixels by 53 pixels and has a single row of 3 images. That means to find the width of each image you should divide 183 by 3.

![GitHub Logo](/resources/player_plane.png)

* Make sure the origin is set to 0,0
* Make sure the background color of white is set to transparent by using the menu option "Erase a color" in the sprite editor menu

## Create the player object

* Create a player object called "obj_player" and assign the sprite from the previous step

## Create the test room

* Create the test room called "room_test"
* Set the speed of the room to 60
* Add the player object to the middle of the room near the bottom

## Create the player initialize script for the player object

* For the "obj_player" object, create a blank script for the "Create" event
* Initialize a new variable `plane_speed` to a value of 10
* Set the `x` variable to the middle of the room and the y variable so that the plane is in the bottom third of the screen
  * Hint: Use `screen_width` and `screen_height` to set `x` and `y`
  * Hint: Don't forget to include a modification for the offset of the sprite (set to 0,0) and the `sprite_width`

## Create the player movement script for the player object

* Create a blank script for the "Step" event
* Add code to make the player respond to the each of the arrow keys (left, right, up and down)
  * You will need to use the `keyboard_check()` function to always move while the key is held down
  * You will need to use the constants `vk_up`, `vk_down`, `vk_left` and `vk_right` with `keyboard_check()`

  * Depending on the direction you will need to increase or decrease the `x` and `y` variables by the `plane_speed` variable when a key is down

*example of checking for down key pressed and adjusting the y position*

```
if keyboard_check(vk_down)
{
  y = y + plane_speed
}
```

## Stop player from moving off the screen

The next part is to stop the player from moving off the screen in any direction
  * You will need to use the following variables for the checks
    * `room_width`, `room_height`, `sprite_width` and `sprite_height`
    * Remember when checking to see if moving off the screen in certain directions you need to use the `sprite_width` and `sprite_height` because the origin of the sprite is set to 0,0
    * You will also need to include those variables when setting the `x` or `y` positions to keep the player sprite on screen

*example of checking if player has gone off the right edge of the room*

```
if (x > room_width - sprite_width)
{
  x = room_width - sprite_width
}
```



