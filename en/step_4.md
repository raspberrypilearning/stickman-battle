## Return to a ready stance

Right now the fighter freezes on the last frame of whatever move it just did. Real fighters keep bobbing, ready for the next attack. You'll add a gentle idle animation and make every move hand back to it when it finishes.

> [!TASK]
>
> Build the idle. It plays the four `idle` frames over and over until the player presses a key, so the fighter breathes while it waits.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> when I receive (fight v)
> repeat until <key (any v) pressed?>
> switch costume to (idle_01 v)
> wait (0.01) seconds
> switch costume to (idle_02 v)
> wait (0.01) seconds
> switch costume to (idle_03 v)
> wait (0.01) seconds
> switch costume to (idle_04 v)
> wait (0.02) seconds
> end
> ```

> [!TIP]
>
> A `broadcast`{:class="block3events"} is a message any script can listen for with `when I receive`{:class="block3events"}. It lets one part of your game trigger another without them being joined together — here, a finished move will tell the fighter, "go back to idle."

> [!TASK]
>
> Make each move end by sending the `fight`{:class="block3events"} message. Add `broadcast (fight v)`{:class="block3events"} as the very last block of `punch`{:class="block3custom"}.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
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
> +broadcast (fight v)
> ```

> [!TASK]
>
> Add the same `broadcast (fight v)`{:class="block3events"} block to the end of `kick`{:class="block3custom"}, `sword`{:class="block3custom"}, `jump`{:class="block3custom"}, and `roll`{:class="block3custom"} too.

**Test:** Click the green flag and press `space`{:class="block3sensing"}. The fighter punches, then bobs in an idle stance until you press another key.
