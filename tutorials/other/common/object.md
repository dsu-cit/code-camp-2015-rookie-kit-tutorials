# File: tps/common/object.py

All parts in the game are objects.  This includes
[player](player.md)s, [npc](npc.md)s, [missile](missile.md)s, and [wall](wall.md)s.  That means
the methods documented here can be used on any
of these objects.

Do not make changes to this file.  You will break
your program if you do.

Information methods available for all ObjectData
------------------------------------------------

* `get_px()` x position, rounded to nearest integer.
  This is intended for use in the display functions.
* `get_py()` y position, rounded to nearest integer.
  This is intended for use in the display functions.
* `get_pw()` width, rounded to nearest integer.
  This is intended for use in the display functions.
* `get_ph()` height, rounded to nearest integer.
  This is intended for use in the display functions.
* `get_pdistance()` distance traveled, rounded to nearest integer.
  This is intended for use in the display functions.
* `get_x()` x position.  This is a float, not suitable
  for use with the display code.
* `get_y()` y position.  This is a float, not suitable
  for use with the display code.
* `get_w()` width.  This is a float, not suitable
  for use with the display code.
* `get_h()` height.  This is a float, not suitable
  for use with the display code.
* `get_center()` (x,y) pair of center of rectangle.
  This is a float, not suitable
  for use with the display code.
* `get_rotation(reverse=False)` returns the rotation of the object in degrees.
  This returns an int value and can be used for display functions. Set reverse to `True` if you need to reverse the rotation. (ie `get_rotation()` or `get_rotation(True)`)
* `get_dx()` fraction of speed in the x direction.
  This is a float number between -1.0 and 1.0.
* `get_dy()` fraction of speed in the y direction.
  This is a float number between -1.0 and 1.0.
* `get_distance()` distance traveled.  This is a float.
* `get_speed()` speed. This is a float.  It is the
  magnitude of the objects speed.  Multiply by
  dx or dy to get the speed in x or y direction.
* `get_state()` STATE_ALIVE, STATE_DYING, or STATE_DEAD.
* `is_alive()` True if alive.
* `is_dying()` True if dying (0 health, but not removed from game).
  Dying objects stay around for DYING_TIME seconds.
* `is_dead()` True if dead (0 health, being removed from game).
* `get_health()` health amount.
* `get_max_health()` maximum health amount.
* `get_dying_percent()` a number from 0 to 1.
  Each object spends 3 seconds in the "dying" state.  This tells
  how much of that 3 seconds has passed
