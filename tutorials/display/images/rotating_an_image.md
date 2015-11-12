# Rotating an image in PyGame

## 1. Load the image

To rotate an image you will have to load an image using the [pygame.image.load](https://www.pygame.org/docs/ref/image.html#pygame.image.load) function and the use the [pygame.transform.rotate](https://www.pygame.org/docs/ref/transform.html#pygame.transform.rotate) function. Refer to [Loading an image for an object](loading_an_image.md) tutorial for more information loading an image.

	file_path = os.path.join('display', 'images', 'my_image_name.png')
	image = pygame.image.load(file_path)
	image = image.convert_alpha() # might not be nessesary depending on OS

Remember that the `surface` and `obj` are available as parameters in the display functions.

## 2. Rotate the image

The `pygame.transform.rotate()` takes a surface object, in our case the `image` we loaded above and a `angle` in degrees.

The `obj` has several methods, but the one we care about for rotating the image is `get_rotation()`. See [Object documentation](../../other/common/object.md) for more information on this method.

	angle = obj.get_rotation()
	image = pygame.transform.rotate(image, angle)

**Note:** Your image should face RIGHT for 0 degrees. If your image is displaying the opposite direction you can reverse it by using:
	
	angle = obj.get_rotation(True)


## 3. Display the rotated image

After rotating the image we can then blit it to the screen, remember to get the `rect` for the `obj` using the `obj_to_rect(obj)` method.

	rect = self.obj_to_rect(obj)
	surface.blit(image, rect)


## Finishing Up

Here is an example of loading an image and resizing it to fit an object. 

	file_path = os.path.join('display', 'images', 'my_image_name.png')
	image = pygame.image.load(file_path)
	image = image.convert_alpha() # might not be nessesary depending on OS
	
	angle = obj.get_rotation()
	image = pygame.transform.rotate(image, angle)

	rect = self.obj_to_rect(obj)
	surface.blit(image, rect)