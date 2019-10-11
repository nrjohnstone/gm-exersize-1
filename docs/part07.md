# Explosions

The goal is to have the player and enemies have an animated explosion when they die

## Add explosion sprite

* Create a sprite called "spr_explosion_1" in Game Maker and load the sprite "explosion0_64x64.png" from the resources folder
* The sprite is a sprite map so you will need to use the "Create from strip" menu item in Game Maker
  * The sheet is 256 pixels by 256 pixels and has a 4 rows of 4 images. You need to calculate the width and height and enter them.

![](/resources/explosion0_64x64.png)

* Make sure the origin of the sprite is centered, this means it should be X=32 and Y=32

## Create object for explosion

* Create an object called "obj_explosion_1" and assign the sprite from above to it
* Add a script to the "Create" event for the explosion and set the animation speed to 0.4
```C
image_speed = 0.4
```
* Add a script to the "Step" event for the explosion object so that it destroys itself when it reaches the end of the animation.
  * The `image_index` is the variable that contains the current image being displayed out of an animated sprite
  * The `image_number` is the total number of images the animated sprite contains
```C
// If the current image is equal to or greater than the number
// of images in the sprite map
if (image_index >= image_number)
{
    // Calling instance_destroy with no parameters destroys the 
    // current instance
    instance_destroy()
}
```

## Make the enemy planes play the explosion animation

* Open the "obj_enemy_plane_1" and open the script that checks the `is_dead` variable and destroys the instance
* In this conditional add some code to create the explosion object. You have to create the explosion object before you destroy the instance of the enemy plane !
* To make sure the explosion is centered over the plane, we need to calculate the x and y of the explosion so that the 
* Here is what your code should look like after you have added the `instance_create` function to create the object

```C
/// Death

if (is_dead)
{
    inst_explosion = instance_create(x, y, obj_explosion_1);  
    // Move the explosion x and y so it is centered 
    // over the current instance 
    inst_explosion.x = x - obj_explosion_1.sprite_xoffset + sprite_xoffset
    inst_explosion.y = y - obj_explosion_1.sprite_yoffset + sprite_yoffset
       
    instance_destroy()
}
```

## Make the player object play the explosion animation

* Open the "obj_player" and make similar changes as you did for the enemy plane so that the explosion is created when the player dies
