## Return to a ready stance

Add an idle animation that the fighter returns to after each move.

> [!TASK]
>
> On the **player** sprite, add a `when I receive`{:class="block3events"} block. In its menu, choose **New message** and name it `ready`{:class="block3events"}.
>
> Add a `repeat until`{:class="block3control"} block with `key any pressed?`{:class="block3sensing"} as its condition. The loop will run while the fighter is waiting for the next key press.
>
> ```blocks3
> when I receive (ready v)
> repeat until <key (any v) pressed?>
> end
> ```

> [!TASK]
>
> Inside the loop, cycle through the four **idle** costumes with a short wait after each one. This makes the fighter move up and down a little while it waits.
>
> ```blocks3
> when I receive (ready v)
> repeat until <key (any v) pressed?>
> +switch costume to (idle_01 v)
> +wait (0.01) seconds
> +switch costume to (idle_02 v)
> +wait (0.01) seconds
> +switch costume to (idle_03 v)
> +wait (0.01) seconds
> +switch costume to (idle_04 v)
> +wait (0.02) seconds
> end
> ```

The idle animation will start when another script broadcasts the `ready`{:class="block3events"} message.

> [!TASK]
>
> Add `broadcast ready`{:class="block3events"} to the end of `punch`{:class="block3myblocks"}. This tells the idle animation to start again.
>
> ```blocks3
> define punch
> start sound (Tennis Hit v)
> switch costume to (punch_01 v)
> wait (0.01) seconds
> switch costume to (punch_02 v)
> wait (0.01) seconds
> switch costume to (punch_03 v)
> wait (0.01) seconds
> switch costume to (punch_04 v)
> wait (0.01) seconds
> switch costume to (punch_05 v)
> wait (0.01) seconds
> switch costume to (punch_06 v)
> wait (0.01) seconds
> switch costume to (punch_02 v)
> wait (0.01) seconds
> switch costume to (punch_01 v)
> wait (0.02) seconds
> +broadcast (ready v)
> ```

**Test:** Click the green flag and press `space`{:class="block3events"}. The fighter should punch, then return to its idle animation.

> [!TASK]
>
> Add `broadcast ready`{:class="block3events"} to the end of `kick`{:class="block3myblocks"}, `sword`{:class="block3myblocks"}, `jump`{:class="block3myblocks"}, and `roll`{:class="block3myblocks"}.

**Test:** Press each move key. After every move, the fighter should return to its idle animation.
