# Timers, Take 2

I guess you can say the `Wait()` function is a sort of timer. It times how long to pause the game.  But what if we want to do something every once in a while.  Let's say, for instance, that we want to have a flashing red light.  One way to do this would be to have an animated background image, like we did in [Chapter 3](../../part1/chapter3/animating_bg.html), but that wouldn't be as much fun (and wouldn't teach you about timers). So, let's create a flashing red light in the Long Room.

We need two new sprites to create a flashing light: one image of the light in the off position, and one image of the light in all of its on-ness glory.  Double-click on **Sprites** in the Project Tree and click on the **Objects** folder. You should see our bathroom door in there.  Add two new objects from the file named *RedLight.png*. Be sure to import the two lights as separate sprites.  The black one will be the "off" light and the red one will be "on". Edit the Long Room and add a new object.  Choose the "off" light and then add another new object choosing the "on" light.  Place both objects at postion (157, 23) in the room so that they're on top of each other.  Give them proper names (`oOffLight` and `oOnLight` will work) and descriptions and change the "on" light's `Visible` property to `False`. We want only the "off" light to be visible at first.

Now for the fun part: Add a function for the room's `Repeatedly Execute` event. We talked about this event in [Chapter 4](../../part1/chapter4/npc.html#repeatedly-execute). If you don't remember how to add it, click on the lightning bolt icon for the room and click the ellipses next to `Repeatedly Execute`. A new function called `room_RepExec()` will be created and you should end up in the script editor. Now, find the `room_AfterFadeIn()` function. In this function we're going to start a new timer that will make the light flash.  Add the following line at the end of the function:
```agsscript
SetTimer(1, 40);
```
Now find the `room_RepExec()` function and add the following code to it:

```agsscript
function room_RepExec()
{
  if( IsTimerExpired(1)  )
  {
    if( oOffLight.Visible  )
    {
      oOffLight.Visible = false;
      oOnLight.Visible = true;
    }
    else
    {
      oOffLight.Visible = true;
      oOnLight.Visible = false;
    }
    SetTimer(1, 40);
  } 
}
```

So, what exactly did we just do?  When the room first loads we started a timer that goes off in one second by calling the `SetTimer()` function. This function takes a number to use as an ID for the timer and a number that tells it when to go off in game loops.  We chose ID number 1 because we don't have any other timers and because we're number 1, obviously. In the `room_RepExec()` function, which runs continuously in the background, we check to see if our timer has gone off by calling the `IsTimerExpired()` function. This function takes a timer ID and returns `true` if that timer has gone off.  If we determine that our timer has gone off, then we check the status of the "off" light.  (We could check the status of any light.  It doesn't really matter.) If the "off" light object is visible, then the light is off and we need to turn it on by making the "off" light invisible and the "on" light visible, otherwise we do the opposite.  Then we restart our timer.  Simple.  Run the game and go into that room. Pretty cool eh?

> **Side Note:** Not only could we have used animated backgrounds to make this work without having to create a timer, but we could also have created one object instead of two.  If we create one object, we would assign two views to it and switch the views instead of making objects appear and disappear.

