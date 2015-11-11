# Adding Sound Effects with PyGame

Chances are you want to add sound effects in your game. If this is the case you probably want several sound effects that play several times. (ie when you fire a missile or when a missile hits a target). **This is only for sound effects; NOT BACKGROUND MUSIC.** If you want to add background music see [Adding Background Music](adding_background_music.md).

Sound effects are added and controlled using [pygame.mixer.Sound](http://pygame.org/docs/ref/mixer.html#pygame.mixer.Sound) objects. Pygame only supports wav and ogg files so if you have mp3 or other filetypes you will have to convert them using software such as [Audacity](http://audacityteam.org/) or using an online tool like [audio-online-convert.com](http://audio.online-convert.com/). Sounds are pretty easy to add and play using the following steps: (a) load and store the sound (b) play the sound.

	sound = pygame.mixer.Sound('path_to_some_ogg_or_wav_file')
	sound.play()
