# Adding Background Music with PyGame

If you want to add some background in your game you have come to the right place. **This is only for adding background music; NOT SOUND EFFECTS.** If you want to add sound effects see [Adding Sound Effects](adding_sound_effects.md).

Music is added and controlled using [pygame.mixer.music](http://pygame.org/docs/ref/music.html#module-pygame.mixer.music) module in PyGame. PyGame has limited support for MP3 files should you should consider using OGG files. If you have MP3 or other sound file types you will want to convert them using software such as [Audacity](http://audacityteam.org/) or an online tool like [audio-online-convert.com](http://audio.online-convert.com/). Music is really easy to add and play using the following steps: (a) initialize the pygame mixer module. *You might not have to do this* (b) load the music file (c) play the sound.

	pygame.mixer.init()
	pygame.mixer.music.load('path_to_ogg_music_file')
	pygame.mixer.music.play()

I called the above code in my `Display.__init__()` method in *client_pygame > display > display.py*. There are several other features supported in the [pygame.mixer.music](http://pygame.org/docs/ref/music.html#module-pygame.mixer.music) module for setting the volume, queuing multiple songs, stopping, rewinding, pausing, and much more to fit your needs.

If you simply want to loop your music then call the `play()` method from the code above like this.

	pygame.mixer.music.play(-1)