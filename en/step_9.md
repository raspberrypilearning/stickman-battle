## Land hits and take damage

Make enemies bite the fighter, and make the fighter's strikes knock enemies away.

> [!TASK]
>
> Make a variable called `health`{:class="block3variables"} and **tick** it so the player can see it on the stage.
>
> ![The health variable ticked in the Variables palette.](images/variable-health.png)

> [!TASK]
>
> Stop the project, then select the **player** sprite.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> Make a `hurt`{:class="block3myblocks"} block that plays the hurt costumes and knocks the fighter back a little.
>
> ```blocks3
> define hurt
> start sound (Crunch v)
> move (-2) steps
> switch costume to (hurt_01 v)
> wait (0.01) seconds
> switch costume to (hurt_02 v)
> wait (0.01) seconds
> switch costume to (hurt_03 v)
> wait (0.02) seconds
> broadcast (ready v)
> ```

> [!TASK]
>
> Add a `when I receive`{:class="block3events"} block. Choose **New message**, name it `hurt`{:class="block3events"}, and run `hurt`{:class="block3myblocks"} from it.
>
> ```blocks3
> when I receive (hurt v)
> hurt :: custom
> ```

> [!TASK]
>
> Select the **enemy** sprite and open the **Sounds** tab.
>
> <p align="center"><img src="images/enemy-labelled.png" alt="Enemy sprite icon labelled enemy." width="100" height="100" style="object-fit: contain;"></p>
>
> Add a bite sound and a knock-back sound. The demo uses **Bite** and **Boing**.
>
> ![The Sounds tab at the top-left of the editor.](images/sounds_tab.png)

> [!TASK]
>
> In the **enemy** clone script, add an `if`{:class="block3control"} block after `next costume`{:class="block3looks"}. If the clone touches the **player**, play the bite sound, broadcast `hurt`{:class="block3events"}, change `health`{:class="block3variables"} by `-1`, and delete the clone.
>
> ```blocks3
> when I start as a clone
> show
> repeat until <(playing) = (0)>
> point towards (player v)
> move (2) steps
> next costume
> +if <touching (player v)?> then
> +start sound (Bite v)
> +broadcast (hurt v)
> +change [health v] by (-1)
> +delete this clone
> end
> end
> delete this clone
> ```

**Test:** Click the green flag and let an enemy reach your fighter. It should bite, your fighter should flinch, and `health`{:class="block3variables"} should drop by one.

> [!TASK]
>
> Stop the project and select the **player** sprite. Open **Costumes** and choose a punch, kick, or sword costume that shows the bright colour on the striking fist, foot, or weapon. This is the **strike colour**.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> Use a colour that appears nowhere else on the stage.

> [!TASK]
>
> Go back to the **enemy** sprite.
>
> <p align="center"><img src="images/enemy-labelled.png" alt="Enemy sprite icon labelled enemy." width="100" height="100" style="object-fit: contain;"></p>
>
> Inside `if touching player`{:class="block3control"}, add another `if`{:class="block3control"} choice:
>
> - If the clone touches the strike colour, play the knock-back sound, move it away, and delete it
> - Otherwise, run the bite blocks
>
> Click the colour in `touching color?`{:class="block3sensing"}, choose the eyedropper, and pick the strike colour from the fighter on the stage.
>
> ```blocks3
> when I start as a clone
> show
> repeat until <(playing) = (0)>
> point towards (player v)
> move (2) steps
> next costume
> if <touching (player v)?> then
> +if <touching color [#ffe500]?> then
> +start sound (Boing v)
> +turn right (180) degrees
> +repeat (20)
> +move (20) steps
> end
> +delete this clone
> else
> start sound (Bite v)
> broadcast (hurt v)
> change [health v] by (-1)
> delete this clone
> end
> end
> end
> delete this clone
> ```

**Test:** Turn to face an incoming enemy and strike as it arrives — it should be knocked away. Stand still and it bites instead.

> [!TASK]
>
> Select the **player** sprite and make a `game over`{:class="block3myblocks"} block that plays the game-over costumes and ends the game.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> define game over
> start sound (Dun Dun Dunnn v)
> switch costume to (death_01 v)
> wait (0.01) seconds
> switch costume to (death_02 v)
> wait (0.01) seconds
> switch costume to (death_03 v)
> wait (0.01) seconds
> switch costume to (death_04 v)
> wait (0.5) seconds
> say [GAME OVER] for (2) seconds
> stop [all v]
> ```

> [!TASK]
>
> On the **player**, add another green flag script. Set `health`{:class="block3variables"} to `20` and wait until it drops below `1`.
>
> Stop the other scripts on the sprite so they cannot interrupt the animation. Then set `playing`{:class="block3variables"} to `0` and run `game over`{:class="block3myblocks"}.
>
> ```blocks3
> when green flag clicked
> set [health v] to (20)
> wait until <(health) < (1)>
> stop [other scripts in sprite v]
> set [playing v] to (0)
> game over :: custom
> ```

Setting `playing`{:class="block3variables"} to `0` tells the other scripts that the game has ended.

**Test:** Play until your health runs out. The fighter should play the game-over animation, show **GAME OVER**, and stop the game.
