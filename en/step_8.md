## Land hits and take damage

Now for the actual fight. You'll make enemies hurt your fighter when they reach it, then make your strikes knock them away. Build it up a piece at a time and test as you go.

> [!TASK]
>
> Make a variable called `health`{:class="block3variables"} and **tick** it so the player can see it on the stage.
>
> ![The health variable ticked in the Variables palette.](images/variable-health.png)

> [!TASK]
>
> First, give your fighter a reaction to being bitten. Build a `hurt`{:class="block3custom"} block that plays the hurt frames and knocks the fighter back a little.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
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
> broadcast (fight v)
> ```

> [!TASK]
>
> Run that block whenever the `hurt`{:class="block3events"} message arrives. This is a new message too — make it from the `when I receive`{:class="block3events"} dropdown with **New message**, named `hurt`{:class="block3events"}.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> when I receive (hurt v)
> hurt :: custom
> ```

> [!TASK]
>
> Your enemy needs two sounds. Open the enemy's **Sounds** tab and add one for when it bites your fighter and one for when it's knocked back. The demo uses `Bite`{:class="block3sound"} and `Boing`{:class="block3sound"}.
>
> ![The Sounds tab at the top-left of the editor.](images/sounds_tab.png)

> [!TASK]
>
> Make an enemy bite when it reaches your fighter. On the enemy's clone script, add a check just after `next costume`{:class="block3looks"}: if the clone is touching your fighter, play the bite sound, send the `hurt`{:class="block3events"} message, take a point of `health`{:class="block3variables"}, and delete the clone.
>
> <p align="center"><img src="images/enemy.png" alt="Enemy sprite icon." width="100" height="100" style="object-fit: contain;"></p>
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
> Now let your fighter fight back. Wrap the bite in a choice: **if** the clone is touching your fighter's **strike colour**, knock it away and destroy it; move your existing bite blocks into the `else`{:class="block3control"} branch.
>
> <p align="center"><img src="images/enemy.png" alt="Enemy sprite icon." width="100" height="100" style="object-fit: contain;"></p>
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

> [!TASK]
>
> Set the strike colour. Click the colour in `touching color [ ]?`{:class="block3sensing"}, choose the eyedropper, and pick the bright colour that shows on your fighter's fists during a strike. The demo uses a bright yellow.

> [!TIP]
>
> Deciding whether two things are touching by looking at a colour is called **colour collision detection**. Because your fighter's fists only flash the strike colour while punching, kicking, or slashing, the enemy is only knocked back when your fighter is *actually* mid-attack — otherwise it lands a bite. Pick a strike colour that appears **nowhere else** on the stage, or the enemy will think it's being hit when it isn't.

**Test:** Turn to face an incoming enemy and strike as it arrives — it should be knocked away. Stand still and it bites instead.

> [!TASK]
>
> Build a `death`{:class="block3custom"} block that plays the death frames and ends the game.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> define death
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
> Add one more green flag script to your fighter. It fills up the health, waits for it to run out, switches the game off, then plays the death animation.
>
> <p align="center"><img src="images/player.png" alt="Player sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> when green flag clicked
> set [health v] to (20)
> wait until <(health) < (1)>
> set [playing v] to (0)
> death :: custom
> ```

> [!TIP]
>
> The rule that ends a game is its **lose condition**. Here it's "health drops below 1". Setting `playing`{:class="block3variables"} to `0` first tells every other script the round is over, so the enemies stop spawning and the fighter stops taking input.

**Test:** Play until your health runs out. Your fighter should play its death animation, show **GAME OVER**, and the game should stop.
