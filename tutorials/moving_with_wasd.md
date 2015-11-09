### Moving and Stopping with "W, A, S ,D"

In most games the player's movement is controlled with W, A, S, and D instead of the UP, LEFT, DOWN, and RIGHT arrow keys. The reason for this is it frees up your right hand so you can add another method of control. It makes it so you can easily hit the spacebar while moving your player to fire a bullet or jump (usually).

We can easily implement this by updating our `game_input_controls` method in the *client_pygame > control > control.py* file.

I started by deleting all the default controls except the `pygame.K_SPACE` which fires the missile when you hit the spacebar, and the `pygame.K_i` key which toggles the game information on and off when you hit the letter i. You might want to comment out all of the code rather than deleting it so you can come back later and use it as a reference.

The following code is what I deleted from the `game_input_controls` method.

    if pygame.K_UP in newkeys:
        engine.set_player_direction(270)
        engine.set_missile_direction(270)
    elif pygame.K_DOWN in newkeys:
        engine.set_player_direction(90)
        engine.set_missile_direction(90)
    elif pygame.K_LEFT in newkeys:
        engine.set_player_direction(180)
        engine.set_missile_direction(180)
    elif pygame.K_RIGHT in newkeys:
        engine.set_player_direction(0)
        engine.set_missile_direction(0)

    if pygame.K_1 in newkeys:
        engine.set_player_speed_stop()
    elif pygame.K_2 in newkeys:
        engine.set_player_speed_slow()
        
    if pygame.K_q in newkeys:
        engine.set_missile_range_none()
    elif pygame.K_w in newkeys:
        engine.set_missile_range_short()

    if pygame.K_a in newkeys:
        engine.set_missile_power_none()
    elif pygame.K_s in newkeys:
        engine.set_missile_power_low()

The following is what I added in its place.

    # Starting Direction
    degrees = 270  #RIGHT = 0, DOWN = 90, LEFT = 180, UP = 270

    if pygame.K_w in keys: #forward
        rotation = (degrees + 0) % 360
        engine.set_player_direction( rotation )
        engine.set_missile_direction( rotation )
        engine.set_player_speed_slow()
    elif pygame.K_d in keys: #right
        rotation = (degrees + 90) % 360
        engine.set_player_direction( rotation )
        engine.set_missile_direction( rotation )
        engine.set_player_speed_slow()
    elif pygame.K_s in keys: #reverse
        rotation = (degrees + 180) % 360
        engine.set_player_direction( rotation )
        engine.set_missile_direction( rotation )
        engine.set_player_speed_slow()
    elif pygame.K_a in keys: #left
        rotation = (degrees + 270) % 360
        engine.set_player_direction( rotation )
        engine.set_missile_direction( rotation )
        engine.set_player_speed_slow()
    else:
        engine.set_player_speed_stop()

**Note:** You will notice I used the `keys` parameter instead of the `newkeys` parameter. This checks to make sure the letter w is being pressed down, where `newkeys` checks for any new keys might have been pressed since the last loop. We need to use `keys` to check for any key that might be held down for an extended period or the method will stop checking for them.

I added the `degrees` variable so I could define my starting direction. I assigned it the value `270` because I want my player to move forward when I push `w`, left when I push `a`, down when I push `s`, and right when I push `d`. All you need to do is add the additional degrees (90, 180, 270) to the players direction _(The degrees variable)_. Since we are adding additional degrees to the previous amount we need to make sure our rotation is still in the range `0-360` by doing a modulus of 360. This also sets things up so we calculate a direction in degrees and update that value easily. See [Mouse Steering](mouse_steering.md) for more information on controlling the rotation of your player.
