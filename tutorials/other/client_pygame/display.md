# File: client_pygame/display/display.py

This class controls all of the drawing of the screen for your game.  The process of drawing a screen is to first draw the background, and then draw everything that goes on top of it.  If two items are drawn in the same place, then the last item drawn will be the one that is visible.

The screen is a 2 dimensional grid of pixels, with the origin (0,0) located at the top-left of the screen, and x values increase to the right and y values increase as you go down.  The y values are opposite of what you learned in your math classes.

[Documentation on drawing in pygame is available here](http://www.pygame.org/docs/ref/draw.html)


## `__init__()`

The `__init__` method creates data members (variables) that are used
in the rest of the methods of this class.  This is
useful for defining colors and sizes, loading image
or sound files, creating fonts, etc.  Basically,
any one time setup.

### Default Data Members include:

#### Font Options

*	`self.font_size` the default font size used to render text
*	`self.font` the default font. *(You must create additional fonts if you want to have multiple font sizes)*

There are other fonts available, but they are not
the same on every computer.  You can read more about
[PyGame Fonts here](http://www.pygame.org/docs/ref/font.html)


#### Colors

*	`self.player_color` the default player color "Green"
*	`self.opponent_color` the default opponent color "Red"
*	`self.missile_color` the default missile color "Cyan"
*	`self.npc_color` the default NPC color "Yellow"
*	`self.wall_color` the default wall color "White"
*	`self.text_color` the default text color "White"
*	`self.background_color` the default background color "Black"

Colors are specified as a triple of integers from 0 to 255.
The values are how much red, green, and blue to use in the color.
Check out [colorpicker.com](http://www.colorpicker.com/) if you want to try out
colors and find their RGB values.  Be sure to use the `R`, `G`, `B` values
at the bottom, not the H, S, B values at the 

### Inherited Data Members

The `Display` class is a inherits from `BaseDisplay` located in *client > base_display.py*

*	`self.width` the width of the game window (in pixels)
*	`self.height` the height of the game window (in pixels)



## `paint_pregame()`

The `paint_pregame` method controls the drawing of the screen before
the player has requested to join a game.  This would usually
allow the user to know the options available for joining
games.



## `paint_waiting_for_game()`

The `paint_waiting_for_game` method controls the drawing of the screen
after the player has requested to join a game, but before
the game actually begins.



## `paint_game()`

The `paint_game` method controls the drawing of the screen while the
game is in session.  This is responsible for making
sure that any information, whether graphics, text, or
images are drawn to the screen.



## `paint_game_over()`

The `paint_game_over` method controls the drawing of the screen after
the game has been won, but before the game goes away.
This is a short (3-5 second) period.



## `process_event()`

The `process_event` method controls handling events that occur in the
game, that aren't represented by objects in the game
engine.  This includes things like collisions,
objects dying, etc.  This would be a great place to
play an audio file when missiles hit objects.

Look at [event documentation](../common/event.md).


## `paint_wall()`

The `paint_wall` method controls the drawing of wall objects. A trick to tell the different between outside walls (on the edge) and interior walls is to check to see if their height and width are the same. This method is called for every wall every frame of the game.



## `paint_npc()`

The `paint_npc` method controls the drawing of NPC objects. This method is called for every npc every frame of the game.



## `paint_missile()`

The `paint_missile` method controls the drawing of missile objects. This method is called for every existing missile every frame of the game.



## `paint_player()`

The `paint_player` method controls the drawing of player objects. This method is called for both players every frame of the game.



## `paint_game_status()`

The `paint_game_status` method controls the drawing of the status bar. By default nothing is displayed until the letter "i" is pressed on the keyboard to toggle the `control.show_info` data member. See the `paint_game` method to change that setting.

