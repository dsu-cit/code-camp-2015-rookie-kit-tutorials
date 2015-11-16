## Handling Multiple Sound Instances

Since pygame requires you to store the sound object to trigger its play() method, it is easy to make the mistake of storing redundant sound instances. You can easily create a sound_library in to store and manage sound instances. I added the following method to my `Display` class located in *client_pygame > display > display.py*. Make sure you add a class variable `self.sound_library = {}` to the `__init__()` method or your program will crash. You also need to import the `os` module `import os`

I created a *sounds* folder in my *client_pygame > display* folder and stored all my sound files in there. I used the [os.path.join](https://docs.python.org/2/library/os.path.html#os.path.join) python function to the correct path to the file so my code will work on every operating system. I also used the [os.path.isfile](https://docs.python.org/2/library/os.path.html#os.path.isfile) function to verify my file existed so avoid having my program crash.

    def play_sound(self, sound_file):
    	"""
    	You should create a self.sound_library={} variable in
        your __init__() method, it should be an empty dictionary.
        If you don't, this helper method will crash your program.
    	"""

    	# If the sound_file is in the library play the sound
        if sound_file in self.sound_library:
            sound = self.sound_library[sound_file]
            sound.play()

        # Otherwise create a new one
        else:
            path_to_sound = os.path.join('display', 'sounds', sound_file)

            # check if file exists
            if os.path.isfile(path_to_sound):
                sound = pygame.mixer.Sound(path_to_sound)
                sound.play()

                # Add the sound_file to the sound_library
                self.sound_library[sound_file] = sound
            else:
            	print path_to_sound, 'does not exists'

You can now call a sound effect at any time by issuing a simple command.

	self.play_sound('sound_filename')

**Note:** If you need to call sounds in both the display.py and control.py files then I would suggest adding the play_sound() method and and sound_library in the `Control` class in control.py because the control object is passed as a parameter to all the functions in the `Display` class. So you could easily call the function in control.py as shown above or as the following in display.py

	control.play_sound('sound_filename')