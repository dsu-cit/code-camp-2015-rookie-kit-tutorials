# Loading an image for an object

PyGame supports many image formats including JPG, PNG, GIF, BMP, PCX, TGA, TIF, LBM, PBM, and XPM ([see pygame.image for more details](https://www.pygame.org/docs/ref/image.html)) I used PNG files because they support transparent backgrounds.


## 1. Creating an image

You can create your images using lots of software and [some online tools](https://sketch.io/sketchpad/). We provided installers for [Gimp](http://www.gimp.org/) a free image editing tool similar to Adobe Photoshop.

After you have your image you are ready to move on.

## 2. Make a directory for your images

I created a folder for my images in my `display` folder under `client_pygame`. I called my folder "images".

	client_pygame/display/images/


## 3. Load an image using [pygame.image.load](https://www.pygame.org/docs/ref/image.html#pygame.image.load)

Loading an image in pygame is fairly simple. Probably the hardest part is getting the file path correct which is why I told you where I created my images folder so you could do something similar.

PyGame suggests using the [os.path.join](https://docs.python.org/2/library/os.path.html#os.path.join) function for building your file path so that it will work on Windows, Mac, or Linux. To do this you need to remember to import the python [os](https://docs.python.org/2/library/os.html) module into your display.py file using `import os`.

	file_path = os.path.join('display', 'images', 'my_image_name.png')

Once you have your file_path built, you can then load the image using [pygame.image.load](https://www.pygame.org/docs/ref/image.html#pygame.image.load)

	image = pygame.image.load(file_path)

Depending on your operating system you might need to do use [convert_alpha()](https://www.pygame.org/docs/ref/surface.html#pygame.Surface.convert_alpha) for the image transparency to work correctly.

	image = image.convert_alpha()


## 4. Displaying or "[blit](https://www.pygame.org/docs/ref/surface.html#pygame.Surface.blit)" the image

Once the image is loaded you need to display it on another [surface object](https://www.pygame.org/docs/ref/surface.html). In our case the `surface` object is provided to us in all of the [display.py](../../other/client_pygame/display.md) functions. To display the image we have to perform a [surface.blit()](https://www.pygame.org/docs/ref/surface.html#pygame.Surface.blit) which requires a `surface` and a destination. For the destination we will use the `self.obj_to_rect(obj)` available in the `Display` class.

Remember that the `surface`, `obj` methods are provided to use in most of the draw functions and we created the `image` in the previous steps.

	rect = self.obj_to_rect(obj)
	surface.blit(image, rect)


## Finishing up

Here is an example of how to load an image.

	file_path = os.path.join('display', 'images', 'my_image_name.png')
	image = pygame.image.load(file_path)
	image = image.convert_alpha() # might not be nessesary depending on OS

	rect = self.obj_to_rect(obj)
	surface.blit(image, rect)
