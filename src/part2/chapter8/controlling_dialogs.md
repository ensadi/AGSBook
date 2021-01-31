# Controlling Dialogs with AGS Scripts

We can use the `SetOptionState()` function from within AGS Scripts to turn dialog ptions on and off. We will need to do this when Foxy knocks the apple down.  Here's the thought process.  When the game starts, that option needs to be hidden because Foxy can't ask Dork about the apple until she gets his name.  It's rude otherwise.  If Foxy knocks the apple down before talking to Dork, the option doesn't need to come on after she gets his name, or at all. If Foxy talks to Dork before knocking the apple down, then the option needs to come on.  If Foxy knocks the apple down after talking to Dork, the option needs to turn off and not come on again.

Find the function `oApple_UseInv()` in room 1's script file.  Right above the last line of code, which contains the `Display("Good shot...")` function, put the following line:

```agsscript
dDialog0.SetOptionState(3, eOptionOffForever);
```
Yes, we did say "Forever."  This one line alone accomplishes everything we want to do.  If Foxy talks to Dork before getting the apple, the option will come on because of the line `dDialog0.SetOptionState(3, eOptionOn);` which we put in the Dialog Script. However, that line will have absolutely no effect if Foxy gets the apple before talking to Dork.  In that case, the `eOptionOffForever` argument that we passed in to the `SetOptionState()` function garantees that the option does not come on, even if we tell it to.  This saves us from having to use an `if/else` block to check if Foxy has the apple or not.  Nifty huh?

