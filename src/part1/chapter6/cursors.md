# Mouse Cursors

Cursors. More fun than curses. Players look at the mouse cursors constantly during the game. That's why it's always a good idea to personalize them and help the player stay immersed in the game.  Not that the default cursors are bad, but having something that fits in with the theme of the game is better.

AGS makes it very easy to replace the mouse cursors since they're just sprites, like the sprites we've already seen. Let's replace 2 of the cursors in our game: The `Walk to` and the `Look at` cursors.  We'll leave the other ones to you.  All we have to do is create some new sprites and replace the cursors with them.

Instead of creating a new folder under Sprites, we're going to just the use the pre-made **Cursors** subfolder under the **Defaults** folder.  If you would prefer to put them somewhere else, then feel free. To make the new sprites, we clicked on one of the cursors already there and looked at the Properties Pane to get the `Heigth` and `Width` properties. Then we made the new sprites with the same height and width.  Also, we kept the top-left corner the same color as the background, which will be used to set the transparency color. Of course, we have some sprites already made for you called *foxywalkcursor.png* and *foxylookcursor.png*, which you're welcome to use.

> **Side Note:** We chose to import new sprites and not to replace the cursors already in there, but that is an option, of course.

When the sprites are imported, all that is left to do is to open up **Mouse cursors** in the Project Tree and double-click on **0:Walk to**. Then, in the Properties Pane change the `Image` property to the number for your new sprite.  Do the same thing for the **1:Look at** cursor.  And, that's it! Run the game and check out the new cursors.

> **Side Note:** You can set the cursor's hotspot, or the spot that needs to be touching what is being clicked. By default this is the top-left corner, but you can click the sprite to change it, or set the coordinates in the Properties Pane.

## Animated Cursors

Why have normal, boring, old cursors, when you can make them move?! That's right, let's make an animated cursor.  If you decide to make an animated cursor, keep in mind that the player will be looking at the cursor a lot, so keep them subtle and try not to annoy the player.

Making a cursor animate is very simple.  All you have to do is create some sprites, use the sprites to create a view, then associate that view with the cursor.  You alreay learned how to import sprites and create views, so either go ahead and make your own, or use the sprites we made in the file *foxywalkcursoranimated.png*. 

Use the Sprites editor to import the sprites, then use the Views editor to create a new view called `vFMWalkCursor`.  We imported our sprites into a new folder under **Main** called *Animated Cursors* just to keep them separate.  Once the view is ready, go back to **Mouse cursors** in the Project Tree and double-click on **0:Walk to** (or whichever view you want to chancge.)  In the Properties Pane, notice that there is an `Animate` property.  Set this to `True` then set the `View` property to the number of the new view that you created.  That should do it! Run the game and check it out.
