# Background Music

Background music can give a nice ambiance to any room.  Just like in the movies, proper background music can convey different feelings and change a player's mood.  Let's add some background music to the long, dark, hall to make it seem a bit scary.  Find the file named *music1.mid*. Open the Audio properties in the Project Tree and right-click on Music to add it (name it `aMusic1`.)

Now let's add the music with scripting.  Go to the Longroom's script and find the `room_AfterFadeIn` function. Add the following 2 lines to the top of the function:

```agsscript
AudioChannel *myChannel = aMusic1.Play(eAudioPriorityNormal);
myChannel.Volume = 15;
```

The first line will set the music to play and give back an audio channel.  No need to tell it to repeat since that's the default behavior for music (not for sounds). The second line will set the music volume on the low end for an increased creepiness factor.  With these two lines and adding a call to `aMusic1.Stop()` in the `room_LeaveLeft` function, you'll have your scary, yet soft, music in that room.  Run the game, go into that room, and be afraid...

Some other functions and properties you should be aware of are `System.Volume`, and `Game.SetAudioTypeVolume()`. `System.Volume` is not a function; it's a property like the volume we've seen before, so you just set it equal to a number between 0 and 100 to set overall volume of the game.  This volume is somewhat overridden by the volume set for each sound or music object though. `Game.SetAudioTypeVolume` takes three parameters: the first parameter sets what type of volume to set, which is one of `eAudioTypeSound`, `eAudioTypeMusic`, `eAudioTypeAmbientSound`. Each one will set the volume of the respective type of audio.  The second parameter is a number between 0 and 100 for the actuall volume.  The third parameter is one of `eVolChangeExisting`, `eVolExistingAndFuture`, `eVolSetFutureDefault`. So, the volume of all existing, all existing and any future audio, or just future audio can be set for the type of audio in parameter one.
