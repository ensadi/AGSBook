# General Settings

We briefly touched the General Settings editor at the beginning of this book and promised you that we'll get to it in Chapter 6.  Well, we like to keep our promises, and according to the URL of this page, this is Chapter 6. The General Settings editor can be accessed by double-clicking it from the Project Tree just like any of the other editors.  This editor allows you to specify some of the basic settings for your game, like the resolution, the name, the maximum score the player can achieve, and some other interesting things.  There are lots of options but we're only going to talk about some of them.  We'll talk about other ones as we get to them in later chapters.

## (Basic properties) Section

This section of the General Settings editor sets up generic things about the game itself.
* Color depth -- The color depth setting tells AGS how to interpret your images. The higher the color depth the more colors you can have.  If you set your game to 16-bit color depth, then you shouldn't make any 32-bit drawings to import. 
* Game title -- This is the name that will appear in the window title bar.  It's a good idea to make sure this is actually the name of your game, and it should be by default.
* Maximum possible score -- This will basically set up a globally accessible variable that you can use to display the maximum possible score on the screen.  For example, you can have something at the top left of the screen that says, "0 of 500 points". That 500 can be placed in the variable and accessed anywhere.  The variable's name is `game.total_score`. The current score can be stored in `game.score` using the `GiveScore()` function.
* Old-style letterbox mode -- Make this `True` to show a black ribbon across the top and bottom of the screen.  Why? Because you want to.
* Resolution -- This is the width and height of your game.  Whatever you decide to set this to is what your backgrounds should be drawn with.

## Character movement Section

This section sets up how the character reacts to movement.
* Characters turn before walking -- Setting this to True will make the characters look like they're actually turning to face a new direction and then start walking.  For example, if the main character is facing down and you click above it using the walk icon, it'll change to the **side** loop then the **up** loop before starting to walk.  If the setting was `False`, the character will immediately go from the **down** loop to the **up** loop before starting to walk.
* Characters turn to face direction -- This setting is just like the one above except it's used with the function `FaceLocation()`. If this is `True`, then when `FaceLocation()` is called, the character will go through the proper loops in the view to turn to face the new location.  If it's `False`, then the character will simply change to the new loop immediately.

## Compiler Section

This section sets up how the game executable is created.  The executable is the main file that you double-click to start the game and ends in a *.exe* extension (usually). Compiling is the process by which AGS will read the game data that you've input and the scripts that you've written and put them together (compile them) into a file that is the game itself, which is the game executable. Dave wrote the game executable, and it's the best damn executable ever written, because Dave is such an awesome programmer.  He's a much better programmer than George, that's for sure.  Wait! What?  That's odd since George is writing this section.<br>Hmmm.
* Compress the sprite file -- If you have a large number of sprites in your game, you could end up with a quite large executable.  Turn this option on and your executable will shrink.  Be forewarned though, the game will run a bit slower because it has to uncompress the sprites when it needs them.  At least I think that's what this option does!
* Enable Debug Mode -- This option (true by default) is very helpful while you're developing your game.  It turns on certain shortcuts to help you see some things or move around. It would be wise to turn this option off before distributing your game. Otherwise, I'll totally cheat when I play your game. &lt;evil laugh here&gt;.  Here's a list of what it can do:
   * Press **control-S** to give the main character all inventory items.  This is good for testing, so you don't have to walk around and pick up everything.
   * Press **control-V** to see the game engine's version information.
   * Press **control-A** to see all walkable areas in the room.  You can't move around or do anything but it's helpful sometimes.
   * Press **control-X** and a dialog box will pop up listing all the rooms in the game.  Chose a room and you will immediately be taken there.  Good for testing changes in rooms without actually having to walk there.
   * Press **control-W** to move to the closest walkable area.  If you somehow get stuck in a non-walkable area (like maybe if you use control-X and end up inside a wall) then this will move you to the closest walkable area so you can perform your tests.
* Split resource files into X MB-sized chunks -- Normally, when you compile your game, all the resources (like the sprites for instance) are placed into the executable.  Therefore, the whole game fits into one file.  If that file is too large, then you can split the resources out of it and make them into their own files.  This way, users can download small files instead of one large file.  The files will be split into MB (Megabyte) sections designated by the number you put here.

## Inventory Section

This section has a few settings that change the way the inventory looks and feels.
* Display multiple icons for multiple items -- Setting this option to `True` will show multiple icons in the inventory window if you have more than one of a certain item.  So, if there are three strawberries, and you pick up all three strawberries, you will see three pictures of the strawberries in the inventory window.  If this is `False`, then you'll only see one picture of a strawberry and you'll have to keep track of how many the character actually has in the code. If you want to show some items as multiples and some not, then you'll need to set this to `False` and create multiple objects in your game that represent the same thing.  Assign those objects the same sprites but give them different variable names (like `oStrawberry1` and `oStrawberry2` for example).  Then you can show both objects in the inventory window whereas others will appear only once.
* Override built-in inventory window click handling -- When you click on an item from the inventory window, AGS handles the click by changing the mouse cursor to that item and making that item the current inventory item.  Cycling through the different mouse pointers by right-clicking, you'll see that there's an extra one that is the current inventory item.  Then you can use that item on something else in the game.  So, after all that blabbing...if you don't want AGS to do any of that and you want to handle the click yourself, then set the option to `True`.  AGS will then call a function in your script called `on_mouse_click()` and you can do whatever with it.
* Inventory item cursor hotspot marker -- This option allows you to place a crosshair or other image on inventory items.  The crosshair will appear at the point on the item that you use as the clicking point.  You can have AGS draw a crosshair for you, or you can draw your own and assign it to it.
* Use selected inventory graphic for cursor -- If you keep this `True`, then the cursor will change to the item that you chose.  Depending of course on what you set as your cursor image in the inventory editor.  If you set it to `False`, then the cursor will always look like the default no matter what inventory item you choose.

## Saved Games Section

This section deals with how games are saved and how the computer will treat them.
* Save games folder name -- When a player saves a game it will go into a folder. Normally this folder will be called the same name as the game, but you can change it here if you like.
* Save screenshots in save games -- Turning this on will take a snapshot of were the player is and save it into the saved game file.  That way a screen shot will appear in the file/game explorer of the current position in the game.

## Sound Section

* Play sound when the player gets points -- Give this option a sound and it will play it whenever you use the `GiveScore()` function to add to the player's score.

## Text output Section

This section deals with how text and speech are shown in the game.
* Always display text as speech -- If this option is on then anything displayed with the `Display()` function will appear as speech said by the main character. If it's off, then the text will just appear in the middle of the screen. 
* Anti-alias TTF fonts -- Anti-aliasing makes corners smoother and fonts look better.  Turning this option on will give you better looking true type fonts but will slow the game up slightly.  It's a matter of performance, but it's probably negligible.
* Custom text-window GUI -- We've already said that we'll talk about GUIs later, and we will.  Be patient.  In the meantime, if you, for some reason, [looked ahead](../../part2/chapter8/text_parser.html) and know how to make a GUI, you can use this option to change the default GUI for normal text in the game.  Any text that is spoken or displayed normally will use this GUI.  Leaving it at the default will leave it up to AGS, and it will always choose its own GUI, of course.
* Custom thought bubble GUI -- Just like the option above, this option will set a GUI to use for thinking.  Using the `Character.Think()` function (for example: `cFoxyMonk.Think("Man I'm hot in this robe!")`) will show the thought text using this GUI.
* Write game text Right-to-left -- If you translate your game to a right-to-left language, set this to `True` to make the text appear from right to left instead of left to right.

## Visual Section

* Default transition when changing rooms -- Transitions are fun to play with. AGS can change what transitions are used to go from room to room.  By default, it fades out the old room and then fades in the new one.  That's ok for most people.  However, it also has the following options:
   * Instant -- Don't transition; just instantly show the new room.
   * Dissolve -- The old room will dwindle out and disappear and the new room will dwindle in.
   * BlackBoxOut -- The old room will be engulfed by a black box, and then the new room will appear taking out the black box.  Just go try it.
   * CrossFade -- The new room will fade in as the old one fades out.
* Pixel-perfect click detection -- This is `True` by default and enables AGS to figure out exactly where the player clicks using the correct point on the mouse cursor.  Setting this to `False` will cause AGS to draw a rectangle in the area where the mouse was clicked and choosing the closest thing there as the clicked item.  This is good if you want your game to be less exact for some reason.  Like maybe if the mouse cursor was a shotgun for example, and you want the click to be in the general vicinity of a bunch of stuff you want to destroy.
* When player interface is disabled, GUIs should -- Sometimes the player has to wait for an event to happen and all controls are disabled (like during a cut scene).  In this case, AGS will cause all controls on any GUIs showing to go gray and become un-clickable.  This behavior can be changed, though, to any of the following:
   * Grey out all their controls -- This is the default.
   * Hide all their controls -- Buttons and other controls on the GUIs will simply disappear.
   * Display normally -- Do nothing.  Just leave them be.
   * Be hidden -- GUIs will run away and hide from the player.


