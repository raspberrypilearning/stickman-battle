## Add a dash roll

Add a roll that animates the fighter and moves it quickly out of danger.

> [!TASK]
>
> On the **player** sprite, make a `roll`{:class="block3myblocks"} block. Add a sound, then switch through the five **dash_roll** costumes.
>
> Add `move 5 steps`{:class="block3motion"} before each costume switch so the fighter slides forward during the roll.
>
> ```blocks3
> define roll
> start sound (Rip v)
> move (5) steps
> switch costume to (dash_roll_01 v)
> wait (0.01) seconds
> move (5) steps
> switch costume to (dash_roll_02 v)
> wait (0.01) seconds
> move (5) steps
> switch costume to (dash_roll_03 v)
> wait (0.01) seconds
> move (5) steps
> switch costume to (dash_roll_04 v)
> wait (0.01) seconds
> move (5) steps
> switch costume to (dash_roll_05 v)
> wait (0.02) seconds
> ```

> [!TASK]
>
> Add a `when v key pressed`{:class="block3events"} block to run `roll`{:class="block3myblocks"}.
>
> ```blocks3
> when [v v] key pressed
> roll :: custom
> ```

> [!TASK]
>
> Test the roll. Change all five `move 5 steps`{:class="block3motion"} blocks to the same larger number for a longer dash, or the same smaller number for a shorter dash.

**Test:** Press `v`{:class="block3events"}. The fighter should roll and move smoothly across the stage.
