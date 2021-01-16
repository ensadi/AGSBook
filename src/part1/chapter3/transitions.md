# Room Transitions

Now that Foxy can go to the different rooms in the shack, we need to talk about something called Room Transitions.  This isn't something that's really a feature of AGS but it's something to keep in mind to give your game a little bit of a professional touch.  Right now, when Foxy walks from room to room, as soon as she passes the room edge, Foxy freezes in place and the game immediately moves to the next room and Foxy instantly jumps to the correct (x, y) coordinates in the new room.

Let's pretend like we're a player of your game.  We've just entered the shack for the first time and we're exploring a bit and walking around.  We walk Foxy over near the right side of the screen because we want to see something over there, and BOOM!  We cross the right edge of the room and we're suddenly in another room.  If we didn't know that we just crossed the right edge of the screen, we might be a little confused as to why we're suddenly somewhere else.

A much more elegant alternative would have been, as soon as Foxy crosses the right edge of the screen, she continues to walk off the screen before the room changes and then, when the new room appears, we see Foxy walk into the screen from the left side.  This kind of attention to detail is what will make your game stand out and will give it a bit more of a polished look and feel.

So, how would we go about doing this?  Well, we've really already outlined what we need to do; we just need to write it into the script.

There are two things we need to accomplish here.  First, we said that when Foxy crosses the edge of the screen we want her to continue to walk off the screen instead of just freeze in place before the room changes.  And the second thing we want is, when Foxy enters the new room, she should walk in from the left side of the screen.

## Walking off the screen

Open the room script for the Main Hall room.  Find the function we created in the last section called `room_LeaveRight`. Change that function so it looks like this:

```agsscript
function room_LeaveRight()
{
  cFoxyMonk.Walk(335, cFoxyMonk.y, eBlock, eAnywhere);
  cFoxyMonk.ChangeRoom(4, -15, cFoxyMonk.y);
}
```

You can probably figure out what that Walk statement does.  This is where we tell Foxy to walk off the right edge of the screen before the room changes.  The first two parameters are the `x` and `y` location that we want her to walk to.  We're doing something a little strange with each of these parameters (so pay attention!). Remember back to our background image of this room.  Its dimensions are 320 pixels wide by 200 pixels high.  Why, then, did we choose an x location of 335 to pass to the Walk function?  That's not even within the bounds of the background!  But wait, we want Foxy to walk *off the screen* before she changes rooms so this is ok.  An x location of 335 will give us this effect. But what about that y location?  What the heck is `cFoxyMonk.y`? This simply refers to the current y location of Foxy.  By using this value instead of hard-coding a number, she will walk in a horizontal direction as she walks off the edge of the screen.

The next parameter to the Walk function is the `BlockingStyle`. This tells AGS whether or not to wait for this command to finish before moving on to the next line of scripting.  There are two possible values you can use here: `eBlock` and `eNoBlock`. We're using `eBlock` in this case, because we don't want Foxy to switch rooms until after she has finished walking.

Finally, the last parameter, `WalkWhere`, tells Foxy whether she has to obey the walkable areas we've defined in the room in order to reach her destination.  If we use `eWalkableAreas` here, then Foxy will only walk on the Walkable areas.  This isn't what we want since we're explicitly telling her to walk off the edge of the screen where there's no walkable area defined. So, we'll use the other option for this parameter, `eAnywhere`, which allows Foxy to walk anywhere on the screen (or even off the screen!).

So that takes care of the walking part.  But we also changed the `ChangeRoom` line. As we learned in a previous section, the `ChangeRoom` function takes 3 parameters -- namely, a room number, and an x and y location of where she will be in the new room.  The room number didn't change but we did change the x and y location.  We're using an x location of -15 for the same reason we used 335 for x earlier: we want Foxy to walk into the new room from off the screen, so we need to set her x location to be off the left edge of the screen. This will be her starting location in the new room.  The y location doesn't need to change from room to room, so we can just use `cFoxyMonk.y` for it. So to reiterate:  To walk Foxy **OFF** the screen, tell her to walk completely off the edge of the screen and then set her new (x,y) coordinates (for the new room) also off the screen so that she can start there and walk onto the new screen.  Confused?  Don't worry.  You just need to see it in action, and you'll get it soon enough.

## Walking onto the screen

So that takes care of walking off the screen.  Now we need to handle the situation where Foxy walks back onto the screen in the new room.  Double click **Edit Room** under **Room 4: Longroom** to bring up the room in the editor.  Now, click on the **Events** button to bring up the events tab, and click the ellipses next to `Enters room after fade-in`. This will create a new script function called `room_AfterFadeIn`. Edit that function so it looks like this:

```agsscript
function room_AfterFadeIn()
{
  if(cFoxyMonk.PreviousRoom == 2)
  {
    cFoxyMonk.Walk(23, cFoxyMonk.y, eBlock, eAnywhere);
  
  }
}
```
Here, we're doing two things.  First, we're checking to make sure that the room that Foxy was just in was the Main Hall.  If it was, then we're going to have her walk from her current position to somewhere just inside the room.

```agsscript
if (cFoxyMonk.PreviousRoom == 2)
```

This line does the checking part.  We're using an `if` statement to look at Foxy's `PreviousRoom` attribute to see if she was just in the Main Hall (room 2).  Note the use of the double equals signs.  Double equals signs are used for testing equality, so don't let that throw you.

Next, we have an open curly brace, followed by:

```agsscript
cFoxyMonk.Walk(23, cFoxyMonk.y, eBlock, eAnywhere);
```

This is our good friend the Walk function again.  This should be familiar now, but just for clarity's sake, I'll explain it briefly.  We're telling Foxy to walk to x location 23 but ensuring that her y location doesn't change so she walks in a straight horizontal line.  We don't want anything else to happen until she gets there so we use `eBlock` for the `BlockingStyle`.  And finally, since we're walking outside of our normal walkable areas, we have to use `eAnywhere` as the `WalkWhere` parameter.

That should do it.  Run the game and try it out.  Walk Foxy into the shack then walk to the right to see our transitions in action!  Notice how she walks off the screen to the right, then the screen changes, and we see her walk onto the screen from the left.  Man! How I wish we could do video screenshots!!!

## A Little Scripting Detour...

So far, our functions have been simple.  You have a name for the function preceded by the word **function**, you follow the name with parentheses, and then you put the statements within curly braces like this:

```plaintext
function myFunction()
{
   do something here;
}
```

In the preceding sub-section, we introduced something new: the `if` statement. This statement examines a condition and only does the statements under it if the condition is true.  So to do something only if Foxy is in room 1 we say `if(cFoxyMonk.Room == 1)`. If we want her to do something if she's in any room *except* room 1 `we say if(cFoxyMonk.Room != 1)`. Just like a function, an `if` statement can be a block.  All the statements in an `if` block will execute if the `if` statement is true. Use curly braces to distinguish an `if` block just like you do with a function, like this:

```plaintext
function myFunction()
{
   if(cFoxyMonk.Room == 1)
   {
     do something here;
		do some more;
   }
   if(cFoxyMonk.Room != 1)
   {
		do something else;
   }
}
```

In this example we do two statements if Foxy is in room 1, and we do one other statement if she's not in room 1.  This would be a good time to introduce the `else` clause. An `if` statement can have an `else` clause that happens only if the `if` statement is `false`, like this:

```plaintext
function myFunction()
{
   if(cFoxyMonk.Room == 1)
   {
     do something here;
		do some more;
   }
   else
   {
		do something else;
   }
}
```

This gives us the same function, but we don't have to check the room twice.  If Foxy is in room 1 do the first block, otherwise do the second.

> **Side Note:** If an `if` or `else` clause only has one statement in it, then the curly braces are optional.

Another importan feature of `if` statements is the `else/if` block. You can have one or more of these to test for different cases.  Let's say you want to do one thing if Foxy is in room 1, something else if she's in room 2, and something completely different if she's in any other room.  It would look like this:

```plaintext
function myFunction()
{
   if(cFoxyMonk.Room == 1)
   {
     do something here...
		do some more...
   }
   else if(cFoxyMonk.Room == 2)
		do something else;
   else
		do something completely different;
}
```

One last thing to cover about `if` statements is checking for multiple cases all at once.  Let's say we want to do something if Foxy is in room 1 AND her x coordinate is 35:

```agsscript
if(cFoxyMonk.Room == 1 && cFoxyMonk.x == 35)
```

The double ampersand makes the `if` statement true ONLY if Foxy is in room 1 AND at the x coordinate 35. If we want to do something if EITHER she's in room 1 OR she's in room 2 it would look like this:

```agsscript
if(cFoxyMonk.Room == 1 || cFoxyMonk.Room == 2)
```

The double pipe ( |  ) symbol is an OR.  The `if` statement will be true if Foxy is either in room 1 or room 2.

And finally, here's a table of the tests you can do in an `if` statement:

<table width=100%>
<tr><td><b>Test</b></td><td><b>What</b></td></tr>
<tr><td>==</td><td>Left term is equal to right term</td></tr>
<tr><td>!=</td><td>Left term is not equal to right term</td></tr>
<tr><td>&lt;</td><td>Left term is less than right term</td></tr>
<tr><td>&gt;</td><td>Left term is greater than right term</td></tr>
<tr><td>&lt;=</td><td>Left term is less than or equal to right term</td></tr>
<tr><td>&gt;=</td><td>Left term is greater than or equal to right term</td></tr>
</table>
