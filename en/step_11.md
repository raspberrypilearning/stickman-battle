## Challenge: Make it harder

Add a **difficulty** setting that controls how often enemies appear.

> [!CHALLENGE]
>
> + Can you make a `difficulty`{:class="block3variables"} variable that decides how quickly new enemies spawn?
> + Can you let the player change the difficulty and feel the game get harder?

> [!HINT]
>
> Divide the delay between clones by `difficulty`{:class="block3variables"}. A larger value creates enemies more often.
>
> ```blocks3
> wait ((1) / (difficulty)) seconds
> ```
>
> Set `difficulty`{:class="block3variables"} to a starting value on the green flag. A value of `2` creates an enemy every half second; `4` creates one every quarter second.

> [!HINT]
>
> **Tick** `difficulty`{:class="block3variables"}, then right-click its display on the stage and choose **slider**. The player can set it before the game starts.
>
> ![The difficulty variable ticked in the Variables palette.](images/variable-difficulty.png)

Play-test different values and choose one that feels challenging but fair.
