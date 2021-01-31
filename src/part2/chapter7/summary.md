# Summary

In this chapter, we learned about how to create timers and get random numbers.

* **The Wait() Function** The `Wait()` function allows you to pause the game for a certain amount of time.  It takes game loops as input, which are 40 loops per second.
* **Timers** You can use the `SetTimer()` and `IsTimerExpired()` functions to start a timer and check to see when it goes off.  `SetTimer()` takes an ID and a number of game loops before it expires, and `IsTimerExpired()` takes an ID and checks to see if the timer corresponding to that ID has gone off yet.  Remember to reset the timer with `SetTimer()` if you want to keep it going.
* **The Random() Function** The `Random()` function will return a random number between 0 and the number that is passed into it inclusive.  Remember to store that number in an `int` variable or you will lose it.

