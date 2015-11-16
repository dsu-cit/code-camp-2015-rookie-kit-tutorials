## Handling Multiple Image Instances

Since pygame requires you to store the image object to blit it to the screen, it is easy to make the mistake of storing redundant image/surface instances which can make your game lag. You can easily create an image_library to store and manage multiple instances. I added the following method to my `Display` class located in *client_pygame > display > display.py*. Make sure you add a class variable `self.image_library = {}` to the `__init__()` method or your program will crash. You also need to import the `os` module `import os`

I created an *images* folder in my *client_pygame > display* folder and stored all my image files in there. I used the [os.path.join](https://docs.python.org/2/library/os.path.html#os.path.join) python function to the correct path to the file so my code will work on every operating system. I also used the [os.path.isfile](https://docs.python.org/2/library/os.path.html#os.path.isfile) function to verify my file existed so avoid having my program crash.

    def get_image(self, image_file):
    	"""
    	You should create a self.image_library={} variable in
        your __init__() method, it should be an empty dictionary.
        If you don't, this helper method will crash your program.
    	"""

    	# If the image_file is in the library return the image
        if image_file in self.image_library:
            return self.image_library[image_file]

        # Otherwise create a new one
        path_to_image = os.path.join('display', 'images', image_file)

        # check if file exists
        if os.path.isfile(path_to_image):
            image = pygame.image.load(path_to_image)
            image = image.convert_alpha() # might not be nessesary depending on OS

            # Add the image_file to the image_library
            self.image_library[image_file] = image

            return image
        
        # If an image has not been returned by this point we have an error.
    	print path_to_image, 'does not exists'
        return None

You can now retrieve an image at any time by issuing a simple command, if it hasn't been created yet, it will get created an stored in the image_library, otherwise the instance will be returned for you to use.

	image = self.get_image('image_filename')
    if image:
        surface.blit(image, rect)
