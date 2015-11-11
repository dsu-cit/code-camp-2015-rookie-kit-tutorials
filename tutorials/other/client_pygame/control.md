# File: client_pygame/control/control.py

 This class is where you specify how your player behaves in the game.  You can use key presses, mouse clicks, and mouse motion to receive input from the user.

You can also add calculations in this code to control the behavior of your player based on the state of the game.


## `__init__()`

The `__init__` method is used to create any variables (data members) that you need to remember. This method is only called once when the game starts so you can add data members that you want to persist and can update them through out the game without worrying about them being reset.

`self.show_info` is the only data member by default. It is the state of the status bar. You can set this value to True to display the game info in the status_bar.


## `pregame_control()`

The `pregame_control` is used to get user input before you join a game.  This is most important in deciding what kind of game the user would like to join.


##  `game_input_control()`

The `game_input_control` is used to get user input during a running game.  This is most important in allowing the user to tell your code what they would like to have happen.


## `game_control()`

The `game_control` is used to have your program make calculations and choose what actions to take, without user input.

