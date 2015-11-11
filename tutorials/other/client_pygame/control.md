# File: client_pygame/control/control.py

 This class is where you specify how your player behaves in the game.  You can use key presses, mouse clicks, and mouse motion to receive input from the user.

You can also add calculations in this code to control the behavior of your player based on the state of the game.


## `__init__()`

The `__init__` method is used to create any variables (data members) that you need to remember. This method is only called once when the game starts so you can add data members that you want to persist and can update them through out the game without worrying about them being reset.

`self.show_info` is the only data member by default. It is the state of the status bar. You can set this value to True to display the game info in the status_bar.


## `pregame_control()`

The `pregame_control` is used to get user input before you join a game.  This is most important in deciding what kind of game the user would like to join. This method is called every frame while waiting for the user to decide they want to join a game, and what kind of game they want to join.

Somewhere in this method you should make one of these calls based on the user input.

*	`self.set_state(CONTROL_STATE_WANT_DUAL)`
*	`self.set_state(CONTROL_STATE_WANT_SINGLE)`
*	`self.set_state(CONTROL_STATE_WANT_TOURNAMENT)`
*	`self.set_state(CONTROL_STATE_WANT_VIEW)`

Defaults here are for the user to press 'd' for dual, 's' for single player game, 't' for tournament.

### Method Parameters

*	`engine` is the game engine that contains all of the information about the current game.  It also has all of the control methods that allows you to send commands to the server to control your player. [engine object documentation](../engine_client/game_engine.md)
*	`keys` is the set of all keys that are currently pressed.  This allows your program to know what keys are held down, if you want to implement behavior that repeats when a key is held down.
*	`newkeys` is the set of all keys that were newly pressed since the last time these methods were called.  This allows your program to know what keys were just pressed, if you want to implement behavior that occurs once, when the key is first pressed.
*	`buttons` is the set of all mouse buttons that are currently held down.  Much like keys is for the keyboard.
*	`newbuttons` is the set of mouse buttons that were newly pressed since the last time these methods were called.  Much like newkeys is for the keyboard.
*	`mouse_position` is the current position (x,y) of the mouse.







##  `game_input_control()`

The `game_input_control` is used to get user input during a running game.  This is most important in allowing the user to tell your code what they would like to have happen. This method is called every frame while the game is running.  You should put controls in here to make changes to the game engine based on the user input.


## `game_control()`

The `game_control` is used to have your program make calculations and choose what actions to take, without user input.


## Useful Reasources

*	[More about PyGame Keyboard inputs](http://www.pygame.org/docs/ref/key.html)
*	[More about PyGame Mouse inputs](http://www.pygame.org/docs/ref/mouse.html)
