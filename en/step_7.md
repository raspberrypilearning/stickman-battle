## Move left and right

Move the fighter with the arrow keys, and stop the controls from working before the game starts.

> [!TASK]
>
> On the **player** sprite, add a `when right arrow key pressed`{:class="block3events"} block. Add the blocks below to face right and move across the stage while cycling through the idle costumes.
>
> ```blocks3
> when [right arrow v] key pressed
> if <(playing) = (1)> then
> point in direction (90)
> switch costume to (idle_01 v)
> change x by (2)
> wait (0.01) seconds
> switch costume to (idle_02 v)
> change x by (2)
> wait (0.01) seconds
> switch costume to (idle_03 v)
> change x by (2)
> wait (0.01) seconds
> switch costume to (idle_04 v)
> change x by (2)
> broadcast (ready v)
> end
> ```

The blocks inside `if playing = 1`{:class="block3control"} only run after the intro has finished and the game has started.

> [!TASK]
>
> Right-click the `when right arrow key pressed`{:class="block3events"} script and choose **Duplicate**. On the copy:
>
> - Change the key to `left arrow`{:class="block3events"}.
> - Change the direction to `-90`{:class="block3motion"}.
> - Change every `change x by 2`{:class="block3motion"} block to `change x by -2`{:class="block3motion"}.
>
> ```blocks3
> when [left arrow v] key pressed
> if <(playing) = (1)> then
> point in direction (-90)
> switch costume to (idle_01 v)
> change x by (-2)
> wait (0.01) seconds
> switch costume to (idle_02 v)
> change x by (-2)
> wait (0.01) seconds
> switch costume to (idle_03 v)
> change x by (-2)
> wait (0.01) seconds
> switch costume to (idle_04 v)
> change x by (-2)
> broadcast (ready v)
> end
> ```

**Test:** Click the green flag, wait for the intro, then hold the arrow keys. Your fighter walks left and right and faces the way it's going.

> [!TASK]
>
> In the `when space key pressed`{:class="block3events"} script, place `punch`{:class="block3myblocks"} inside `if playing = 1`{:class="block3control"}.
>
> ```blocks3
> when [space v] key pressed
> +if <(playing) = (1)> then
> punch :: custom
> end
> ```

> [!TASK]
>
> Add the same `if playing = 1`{:class="block3control"} check to the `m`{:class="block3events"}, `n`{:class="block3events"}, `up arrow`{:class="block3events"}, and `v`{:class="block3events"} scripts.

**Test:** Before you press the green flag, tap the keys — nothing should happen. After the intro, every move and both walks should work.
