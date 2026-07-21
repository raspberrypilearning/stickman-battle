## Start the game

At the moment your moves work, but the fighter has no proper start. You'll add a green flag script that sets the fighter up, plays a short intro, then switches the game on — one piece at a time.

> [!TASK]
>
> Make a variable called `playing`{:class="block3variables"}. It's just for the code, so **untick** it to keep it off the stage. You'll use it to remember whether a round is running.
>
> ![The Make a Variable button in the Variables palette.](images/make-a-variable.png)

> [!TIP]
>
> A variable that stores whether the game is running is called a **game state** or a **flag**. Lots of scripts can check the same flag, so they all agree on whether the game has started, is being played, or is over.

> [!TASK]
>
> On the `player`{:class="block3looks"} sprite, start a green flag script that sets the fighter up: a starting costume, in front of everything, in the middle, facing left, at a good size.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> when green flag clicked
> switch costume to (walk_02 v)
> go to [front v] layer
> go to x: (0) y: (0)
> set rotation style [left-right v]
> point in direction (-90)
> set size to (250) %
> ```

> [!TIP]
>
> `set rotation style [left-right v]`{:class="block3motion"} means the sprite only ever flips to face left or right, instead of spinning all the way round when it turns. It's the natural setting for a side-on fighter.

> [!TASK]
>
> Add a short intro to the end of that script: a pause, then two lines your fighter shouts before the fight.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> when green flag clicked
> point in direction (-90)
> set size to (250) %
> +wait (1) seconds
> +say [GOJIRA!!!!] for (2) seconds
> +say [I will punch you into the shadow realm!] for (1.5) seconds
> ```

> [!TASK]
>
> Finally, switch the game on. At the very end, set `playing`{:class="block3variables"} to `1` and start the idle bob with the `fight`{:class="block3events"} message.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> when green flag clicked
> say [I will punch you into the shadow realm!] for (1.5) seconds
> +set [playing v] to (1)
> +broadcast (fight v)
> ```

> [!TASK]
>
> This is your fighter's big entrance, so make it yours. Change the two `say`{:class="block3looks"} lines to whatever your fighter would shout, and change the `set size to`{:class="block3looks"} value if your fighter looks too big or too small.

**Test:** Click the green flag. Your fighter faces left, sizes up, delivers its lines, then settles into the idle bob.
