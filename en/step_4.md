## Return to a ready stance

Right now the fighter freezes on the last frame of whatever move it just did. Real fighters keep bobbing, ready for the next attack. You'll add a gentle idle animation and make every move hand back to it when it finishes.

> [!TASK]
>
> Start a new script on the `player`{:class="block3looks"} sprite. When it receives the `fight`{:class="block3events"} message, it should keep looping until the player presses a key. Build the empty loop first.
>
> This message doesn't exist yet. In the `when I receive`{:class="block3events"} block's dropdown, choose **New message** and name it `fight`{:class="block3events"}.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> when I receive (fight v)
> repeat until <key (any v) pressed?>
> end
> ```

> [!TIP]
>
> A `repeat until`{:class="block3control"} loop runs the blocks inside it over and over until its condition becomes true. Here it stops the instant the player presses any key, so the fighter only idles while it's waiting for the next move.

> [!TASK]
>
> Now fill the loop. Cycle the four `idle` frames with a short wait after each, so the fighter bobs on the spot.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> when I receive (fight v)
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

You won't see the idle run yet — nothing sends the `fight`{:class="block3events"} message. That's what you'll fix next.

> [!TIP]
>
> A `broadcast`{:class="block3events"} is a message any script can listen for with `when I receive`{:class="block3events"}. It lets one part of your game trigger another without them being joined together — here, a finished move will tell the fighter, "go back to idle."

> [!TASK]
>
> Make the punch hand back to the idle when it finishes. Add `broadcast (fight v)`{:class="block3events"} as the very last block of `punch`{:class="block3custom"}.
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

**Test:** Click the green flag and press `space`{:class="block3sensing"}. The fighter punches, then bobs in an idle stance until you press another key.

> [!TASK]
>
> Add the same `broadcast (fight v)`{:class="block3events"} block to the very end of `kick`{:class="block3custom"}, `sword`{:class="block3custom"}, `jump`{:class="block3custom"}, and `roll`{:class="block3custom"} too.

**Test:** Press each attack key in turn. After every move, your fighter should settle back into the idle bob instead of freezing.
