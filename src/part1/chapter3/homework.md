# HOMEWORK

Make 3 more screen transitions: One for going into the bathroom, one for coming back to the main hall from the bathroom, and one for coming back to the main hall from the longroom.  You can also add the same code to the region in room 1 and `afterFadeIn` of room 2 to walk Foxy in from the outside.  Just as a bit of help, here's the final code for the `afterFadeIn` function of room 2.

```agsscript
function room_AfterFadeIn()
{
  if (cFoxyMonk.PreviousRoom == 1)
  {
    cFoxyMonk.Walk(cFoxyMonk.x, 184, eBlock, eAnywhere);
  }
  else if (cFoxyMonk.PreviousRoom == 3)
  {
    cFoxyMonk.Walk(cFoxyMonk.x, 120, eBlock, eAnywhere);
  }
  else if(cFoxyMonk.PreviousRoom == 4)
  {
    cFoxyMonk.Walk(300, cFoxyMonk.y, eBlock, eAnywhere);
  }
}
```
