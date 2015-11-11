# Mouse Steering

The default controls in the game can be kind of hard to use. If you don't update your graphics it is also really difficult to know which way your are facing and you are also limited to moving UP, DOWN, LEFT, and RIGHT. Wouldn't it be nice if you could point your mouse in the direction you want to go, move forward and have it follow your mouse?

In this tutorial we will show how to update your player controls to enable steering with the mouse. This tutorial assumes you are starting with the base kit, so if you are not you may have to make adjustments to fit your game client.

#### Video Example (Click on the image to view video on youtube)

[![Mouse Steering Video](../assets/images/mouse_steering_video.png)](http://www.youtube.com/watch?v=8Z2SukeupgA "Code Camp Rookie Kit - Mouse Steering Example")

### Calculating the angle of rotation

We will need to calculate the angle in degrees from our player to the mouse position. You can learn how to do this by reading the ["Calculating Degrees From Two Points" Tutorial](calculate_degrees.md) which teaches how to calculate angles in radians and degrees using 2 points (x1,y1 and x2,y2). In our case we will use the player's current position for x1,y1 and the mouse position for x2,y2.

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

### Finishing up

I added my updates before checking any keyboard input so we can use the new missile direction and player direction before moving, firing the missile, or anything else.

**Note:** We need to add in a bit of error checking because the player object does not always exist in the game (ie, the game hasn't started, the player dies, or the game is over)

	import math #You might want to do this at the start of the file
	oid = engine.get_player_oid()
	if oid > 0: #check the player object exists
		player = engine.get_object(oid)
		if player != None: #make sure it is not a NoneType object
			#Your code you want to run goes inside this block.
