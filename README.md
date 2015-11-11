# Code Camp Rookie Kit


## Setup

You'll need Python and PyGame installed on your system
to run and change the game.

### Windows/Mac OSX

1.	Download the latest version of Python 2.7 (32-bit version).
	*	**Do not install a 3.x version of python**
	*	**Do not install a 64-bit version of python** (even if your operating system is 64-bit)
	*	[Windows installer - Python](2015-thumbdrive-contents/WINDOWS/python-2.7.10.msi?raw=true)
	*	[OSX installer - Python](2015-thumbdrive-contents/OSX/python-2.7.10-macosx10.6.pkg?raw=true)
2.	Download and install the 32-bit version of PyGame for Python 2.7
	*	[Windows installer - PyGame](2015-thumbdrive-contents/WINDOWS/pygame-1.9.1.win32-py2.7.msi?raw=true)
	*	[OSX installer - PyGame](2015-thumbdrive-contents/OSX/pygame-1.9.1release-python.org-32bit-py2.7-macosx10.3.dmg?raw=true)

*Note:* If you have homebrew on your mac you can use it to install Python and PyGame.

	brew update
	brew install python
	brew install homebrew/python/pygame

### Linux

1.	Install python2.7 using the Package Manager.
2.	Install pygame using the Package Manager.

### Test your system to verify python and pygame work.
	
*	Download and run [pygame_check.py](2015-thumbdrive-contents/pygame_check.py)
*	If you see the following window with Code Camp messages, your system is working ![PyGame Check](assets/images/pygame_check.png)


## Download the Starter Code

[Rookie Kit](2015-thumbdrive-contents/rookie-kit.zip?raw=true)


## Running the Game

You start the game by opening *client_pygame > main.py* and running/building the program. It is important that the folders and files stay named the same and are not moved out of their current structure. If you used the installers from above, you can open the main.py file with IDLE and then "Run" the program.


### The controls

When first running the game, you control the direction the player moves and fires a missile by pushing the UP, DOWN, LEFT, or RIGHT keys. You may notice the player does not move by pushing a direction key. To start the player moving you push the 2 key, and to stop you press 1.

You may change and customize the controls however you want. Below is a list of how programmed by default.

*	`UP` changes the player's move direction and missile direction to up
*	`DOWN` changes the player's move direction and missile direction to down
*	`LEFT` changes the player's move direction and missile direction to left
*	`RIGHT` changes the player's move direction and missile direction to right
*	`1` stops the player's movement
*	`2` starts the player's movement
*	`q` disables the missile's range
*	`w` sets the missile range to 100 pixels
*	`a` disables the missile's damage (fires blanks)
*	`s` sets missile power to do 0.5 hit-points (hp) damage
*	`SPACE` fires a missile (if the player has enough missile mana)
*	`i` toggles the game info in the status bar (hp, move mana, missile mana, etc)


### The game

The game is a basic shooter. You are playing against a single opponent. There are modes to play a single player game (against an AI player), and a 2 player mode to play against someone else at Code Camp.

When you load the game you will see a bunch of square objects with an assortment of colors to help you identify them.

*	Green - Your player
*	Red - The opponent
*	Yellow - NPC (Non-Player Character) players, kill them to level up
*	White - Walls, can hide behind, but they get in the way
*	Light Blue - Missiles

There are NPC players you can shoot to level up your player to gain more missile and move mana (ability to move farther and shoot more bullets) as well as abilities to upgrade your missile power, range, and player speed.

Both you and your opponent start with 30 hit points. The default missile deals 0.5 hp of damage (so you have to shoot your opponent 60 times to kill them). You can customize your game to upgrade your missiles to do more damage, but you have to level up your player by shooting NPC players for this to work.

You can customize the game client by changing the colors, shapes, graphics, controls, sound effects, and anything else you can put your mind to. However, you can't give yourself extra bullets, change your's or your opponent's hit-points, make yourself invisible, speed of the bullets, or change the size of the walls, players, NPCs, that would just be unfair.

Have fun with the Rookie Kit. Don't be scared to ask questions or help your neighbors. We want everyone to have a great time at Code Camp.


## Tutorials

There are several tutorials to help you with your game and we will publish more as needed during Code Camp.

[Rookie Kit Tutorials](tutorials/index.md)


## Discussions

If you have questions, chances are someone else has the same question. Feel free to ask questions on the following discussion board and feel free to answer other questions. Remember to be considerate of others and don't post anything inappropriate or you will be banned, and possibly asked to leave Code Camp.

[Google Group Discussion Forum](https://groups.google.com/forum/#!forum/code-camp-rookie-kit)