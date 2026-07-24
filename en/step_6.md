## Start the game

Add a green flag script that sets up the fighter, plays a short intro, and starts the game.

> [!TASK]
>
> Make a variable called `playing`{:class="block3variables"}. **Untick** it so it does not appear on the stage. It will remember whether the game is running.
>
> ![The Make a Variable button in the Variables palette.](images/make-a-variable.png)
>
> ![The playing variable unticked in the Variables palette.](images/variable-playing.png)

> [!TASK]
>
> On the **player** sprite, add a `when green flag clicked`{:class="block3events"} block and the blocks below. They set the fighter's starting costume, layer, position, direction, and size.
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

`set rotation style left-right`{:class="block3motion"} lets the sprite face left or right without turning upside down.

> [!TASK]
>
> Add a short pause and two lines for your fighter to shout.
>
> ```blocks3
> when green flag clicked
> switch costume to (walk_02 v)
> go to [front v] layer
> go to x: (0) y: (0)
> set rotation style [left-right v]
> point in direction (-90)
> set size to (250) %
> +wait (1) seconds
> +say [GOJIRA!!!!] for (2) seconds
> +say [I will punch you into the shadow realm!] for (1.5) seconds
> ```

> [!TASK]
>
> At the end of the script, set `playing`{:class="block3variables"} to `1` and broadcast `ready`{:class="block3events"} to start the idle animation.
>
> ```blocks3
> when green flag clicked
> switch costume to (walk_02 v)
> go to [front v] layer
> go to x: (0) y: (0)
> set rotation style [left-right v]
> point in direction (-90)
> set size to (250) %
> wait (1) seconds
> say [GOJIRA!!!!] for (2) seconds
> say [I will punch you into the shadow realm!] for (1.5) seconds
> +set [playing v] to (1)
> +broadcast (ready v)
> ```

> [!TASK]
>
> Personalise the two `say`{:class="block3looks"} lines. Change `set size to`{:class="block3looks"} if your fighter looks too big or too small.

**Test:** Click the green flag. Your fighter faces left, sizes up, delivers its lines, then settles into the idle bob.
