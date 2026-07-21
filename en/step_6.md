## Move left and right

A fighter that can't move is an easy target. You'll let the player walk with the arrow keys, and make sure no move works until the game has actually started.

> [!TASK]
>
> Add a script so the `right arrow`{:class="block3sensing"} turns the fighter to face right and walks it across the stage, cycling the idle frames so its legs move.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
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
> broadcast (fight v)
> end
> ```

> [!TASK]
>
> Add the matching `left arrow`{:class="block3sensing"} script. It's the same, but it faces the fighter the other way with `point in direction (-90)`{:class="block3motion"} and walks the other way with `change x by (-2)`{:class="block3motion"}.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
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
> broadcast (fight v)
> end
> ```

**Test:** Click the green flag, wait for the intro, then hold the arrow keys. Your fighter walks left and right and faces the way it's going.

> [!TASK]
>
> Your attacks should only work once the game is running, too. Wrap the `punch`{:class="block3custom"} block in a check so it only fires while `playing`{:class="block3variables"} is `1`.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> when [space v] key pressed
> +if <(playing) = (1)> then
> punch
> end
> ```

> [!TASK]
>
> Do the same for the `m`{:class="block3sensing"}, `n`{:class="block3sensing"}, `up arrow`{:class="block3sensing"}, and `v`{:class="block3sensing"} key scripts, so `kick`{:class="block3custom"}, `sword`{:class="block3custom"}, `jump`{:class="block3custom"}, and `roll`{:class="block3custom"} are all guarded.

> [!TIP]
>
> Checking the game state before acting on a key press is called **guarding input**. It stops the player attacking during the intro or after the game is over, when those moves shouldn't do anything.

**Test:** Before you press the green flag, tap the keys — nothing should happen. After the intro, every move and both walks should work.
