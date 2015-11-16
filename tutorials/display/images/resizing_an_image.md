# Resizing an image in PyGame

**You should not use this to resize large images to fit in your game. You might need to use this if you use the same image for objects of different sizes. Make your images as small as you can to avoid game lag.**

## 1. Load the image

To resize an image you will have to load an image using the [pygame.image.load](https://www.pygame.org/docs/ref/image.html#pygame.image.load) function and the use the [pygame.transform.scale](https://www.pygame.org/docs/ref/transform.html#pygame.transform.scale) function. Refer to [Loading an image for an object](loading_an_image.md) tutorial for more information loading an image.

	file_path = os.path.join('display', 'images', 'my_image_name.png')
	image = pygame.image.load(file_path)
	image = image.convert_alpha() # might not be nessesary depending on OS

Remember that the `surface` and `obj` are available as parameters in the display functions.

## 2. Resize/Scale the image

The `pygame.transform.scale()` takes a surface object, in our case the `image` we loaded above and a tuple with the width and height we want to resize to. The width and height need to be integers.

The `obj` has several methods, but the ones we care about for resizing the image are `get_pw()` the object's width and `get_ph()` the object's height. See [Object documentation](../../other/common/object.md) for more information on those methods.

	width = obj.get_pw()
	height = obj.get_ph()
	image = pygame.transform.scale(image, (width, height))


## 3. Display the resized image

After resizing the image we can then blit it to the screen, remember to get the `rect` for the `obj` using the `obj_to_rect(obj)` method.

	rect = self.obj_to_rect(obj)
	surface.blit(image, rect)


## Finishing Up

Here is an example of loading an image and resizing it to fit an object. 

	file_path = os.path.join('display', 'images', 'my_image_name.png')
	image = pygame.image.load(file_path)
	image = image.convert_alpha() # might not be nessesary depending on OS
	
	width = obj.get_pw()
	height = obj.get_ph()
	image = pygame.transform.scale(image, (width, height))

	rect = self.obj_to_rect(obj)
	surface.blit(image, rect)