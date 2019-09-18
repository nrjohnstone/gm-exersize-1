# Goal

The goal is to end up with a game controller that can handle global co-ordination in the game and keep track of when the player pushes escape to quit the game

## Create the game controller object

* Create an object called "obj_gamecontroller" in Game Maker
* Add a script to the game controller for the "Step" event
* In the script, check for the Escape key being pressed, and if so exit the game
  * You will need to use the function "keyboard_check_pressed" to check when the key has been pressed. The constant for the Escape key is `vk_escape`
  * You will need to use the function game_end() to end the game when the key is pressed