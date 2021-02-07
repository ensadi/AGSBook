# Starting and Ending Cutscenes

Cutscene basics are not complicated.  AGS provides two functions that are used to start and end a cutscene: `StartCutscene()` and `EndCutscene()`.

`StartCutscene()` is used to tell AGS that the following commands are part of a cutscene.  `EndCutscene()` is used to tell AGS that the cutscene is over, and everything after this is normal game play.  The stuff that's between these two functions will comprise the actual cutscene instructions.

Technically, however, you don't need those two functions to create cutscenes.  Since cutscene instructions are just normal, every day, AGS functions, you can just put the inscturctions for your cutscene somewhere and have it run.  The reason for having those two functions is to allow the player to skip the cutscene if he or she wishes.  Players may want to skip a cutscene if it's an intro for example.  They might not want to watch the same intro every time they play the game.

`StartCutscene()` takes exactly one argument: `StartCutscene(CutsceneSkipType)`.   The argument `CutsceneSkipType` can be one of the following:

* `eSkipESCOnly` -- This option allows the player to skip the cutscene by pressing the ESC key.
* `eSkipAnyKey` -- This option allows the player to skip the cutscene by pressing any key.
* `eSkipMouseClick` -- This option allows the player to skip the cutscene using a mouse click.
* `eSkipAnyKeyOrMouseClick` -- This option combines the previous two.  The player can use any key or use a mouse click to skip the cutscene.
* `eSkipESCOrRightButton` -- This option is a combination of the ESC key or the right mouse button.

If the player decides to skip the cutscene, AGS will quickly run through all of the instructions that fall between the `StartCuscene()` and `EndCutscene()` functions. This point is important:  If the cutscene is skipped, AGS will **not** skip over the instructions between the two functions.  The instructions will actually run, but very very fast.  Furthermore, the `EndCutscene()` function will return a value of 0 if the player actually watched the whole cutscene, or 1 if the player skipped it.  The return value can be useful if you want to do something different depending on whether the player watched or skipped the cutscene.

