# Mouse Steering

## Difficulty: Medium

The default controls in the game can be kind of hard to use. If you don't update your graphics it is also really difficult to know which way your are facing and you are also limited to moving UP, DOWN, LEFT, and RIGHT. Wouldn't it be nice if you could point your mouse in the direction you want to go, move forward and have it follow your mouse?

In this tutorial we will show how to update your player controls to enable steering with the mouse. This tutorial assumes you are starting with the base kit, so if you are not you may have to make adjustments to fit your game client.

#### Video Example (Click on the image to view video on youtube)

[![Mouse Steering Video](../assets/images/mouse_steering_video.png)](http://www.youtube.com/watch?v=8Z2SukeupgA "Code Camp Rookie Kit - Mouse Steering Example")

### Explanation

We need a couple bits of information in order to calculate the direction we want to travel. We need the starting position (`x1,y1`) and the position we want to travel towards (`x2,y2`). In our case we will use the player's current position for x1,y1 and the mouse position for x2,y2.

Next we need to calculate the change between the x and y positions. This is often referred to as `dx,dy`. They are calculated separately by taking the position we want to move towards and subtracting the current position. See the image for an illustrated explanation.

	dx = x2 - x1
	dy = y2 - y1

![Calculate dx and dy](../assets/images/mouse_steering_1.png)

Once you have the dx and dy values you can calculate the angle in radians fairly easy. It is usually calculated as atan(dy / dx) but in python we can use the [math.atan2](https://docs.python.org/2/library/math.html#math.atan2) function.

	radians = math.atan2(dy, dx)

_**NOTE:** This will require that you import the math library in your control.py file using `import math`._

We need to make sure we convert the radians for a full circle. So we need to divide the radians by 2&pi; and keep the remainder, or in other words take radians % 2&pi;. In python &pi; can be represented as [math.pi](https://docs.python.org/2/library/math.html#math.pi).

	radians = radians % 2 * math.pi

Finally we can convert from radians to degrees using the [math.degrees](https://docs.python.org/2/library/math.html#math.degrees) function.

	degrees = math.degrees(radians)

So after working through all that we are left with the following.

	import math

	dx = x2 - x1
	dy = y2 - y1
	radians = math.atan2(dy, dx)
	radians = radians % 2 * math.pi
	degrees = math.degrees(radians)


## Implementation

We will implement the following code from above in the `game_input_control` method in *client_pygame > control > controls.py* file.

### 1. Retrieve your the player's current position (x1,y1)

We need to do get the player's position from the PlayerData object. The one trick is we don't have immediate access to the PlayerData object in the `game_input_control` method. We do however have access to the game_engine as `engine`. Using this we can retrieve the PlayerData object. This will then give us access to the `PlayerData.get_center()` method.

This can be accomplished with 3 simple steps.

1. Retrieve and store the player object_id `oid` using the `engine.get_player_oid()` method.
2. Retrieve and store the PlayerData object using the `engine.get_object(oid)` method.
3. Retrieve and store the x and y position of the player using the `PlayerData.get_center()` method.

The code:

	oid = engine.get_player_oid()
	player = engine.get_object(oid)
	(x1,y1) = player.get_center()


### 2. Get the mouse position (x2, y2)

This part is easy because the `mouse_position` is provided to us as a parameter so we don't have to do anything to grab its position. We just have to store is so we can use it.

	(x2,y2) = mouse_position

### 3. Calculate the rotation of the player

Using the explanation above we need to calculate the rotation of the player.
	
	dx = x2-x1
	dy = y2-y1

	radians = math.atan2(dy, dx)
	radians %= 2*math.pi
	degrees = math.degrees(radians)

### 4. Update the nessesary controls.

We need to udate the direction the missile direction and the player direction. We do this using the `engine.set_missile_direction(degrees)` and `engine.set_player_direction(degrees)` methods.

	engine.set_missile_direction(degrees)
	engine.set_player_direction(degrees)

### Finished Code

I added these updates before checking any keyboard input so we can use the new missile direction and player direction before moving, firing the missile, or anything else.

**Note:** We need to add in a bit of error checking because the player object does not always exist in the game (ie, the game hasn't started, the player dies, or the game is over)

	import math #You might want to do this at the start of the file
	oid = engine.get_player_oid()
	if oid > 0: #check the player object exists
		player = engine.get_object(oid)
		if player != None: #make sure it is not a NoneType object

			(x1,y1) = player.get_center()
			(x2,y2) = mouse_position

			dx = x2-x1
			dy = y2-y1

			radians = math.atan2(dy, dx)
			radians %= 2*math.pi
			degrees = math.degrees(radians)

			engine.set_missile_direction(degrees)
			engine.set_player_direction(degrees)

## Additional Features.

### Moving and Stopping with "w"

I don't personally like having to push "1" to stop my guy and "2" to start moving. I would rather hold "w" to move forward and automatically stop moving when I release "w".

To do this, I deleted the following code from the `game_input_controls` method.

	if pygame.K_1 in newkeys:
        engine.set_player_speed_stop()
    elif pygame.K_2 in newkeys:
        engine.set_player_speed_slow()
        
    if pygame.K_q in newkeys:
        engine.set_missile_range_none()
    elif pygame.K_w in newkeys:
        engine.set_missile_range_short()

and added this in its place.

	if pygame.K_w in keys:
		engine.set_player_speed_slow()
	else:
		engine.set_player_speed_stop()

**Note:** You will notice I used the `keys` parameter instead of the `newkeys` parameter. This checks to make sure the letter w is being pressed down, where `newkeys` checks for any new keys might have been pressed since the last loop. We need to use `keys` to check for any key that might be held down for an extended period or the method will stop checking for them.

### Reversing and Strafing

We can easily map Reversing and Strafing controls to the standard WASD. All you need to do is add the additional degrees (90, 180, 270) to the players direction _(The degrees we calculated above)_. Since we are adding additional degrees to the previous amount we need to make sure our rotation is still in the range `0-360` by doing a modulus of 360. We will use the `keys` parameter because each of these keys might be held down.

	if pygame.K_w in keys: #forward
		engine.set_player_direction( degrees )
		engine.set_player_speed_slow()
	elif pygame.K_d in keys: #right
		engine.set_player_direction( (degrees + 90) % 360 )
		engine.set_player_speed_slow()
	elif pygame.K_s in keys: #reverse
		engine.set_player_direction( (degrees + 180) % 360 )
		engine.set_player_speed_slow()
	elif pygame.K_a in keys: #left
		engine.set_player_direction( (degrees + 270) % 360 )
		engine.set_player_speed_slow()
	else:
		engine.set_player_speed_stop()

Now if we hold `w` our player will move towards our mouse, `s` will move away from the mouse, `a` with strafe left _(considering mouse forward)_, and `d` will strafe right _(considering mouse forward)_. But if we fire our missiles they will continue to fire towards the direction of our mouse.