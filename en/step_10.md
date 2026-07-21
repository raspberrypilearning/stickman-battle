## Challenge: make it harder

Your game runs at one speed. Real games let the danger build. Can you add a **difficulty** setting that controls how often enemies appear?

> [!CHALLENGE]
>
> + Can you make a `difficulty`{:class="block3variables"} variable that decides how quickly new enemies spawn?
> + Can you let the player change the difficulty and feel the game get harder?

> [!HINT]
>
> Right now your enemy spawner waits a fixed `1` second between clones. If you divide that wait by a `difficulty`{:class="block3variables"} variable, a bigger number means a shorter wait — so enemies come thick and fast.
>
> <p align="center"><img src="images/enemy.png" alt="Enemy sprite icon." width="100" height="100" style="object-fit: contain;"></p>
>
> ```blocks3
> wait ((1) / (difficulty)) seconds
> ```
>
> A `difficulty`{:class="block3variables"} of `2` spawns an enemy every half second; `4` spawns one every quarter second. Just remember to set `difficulty`{:class="block3variables"} to a starting value on the green flag, or you'll be dividing by nothing.

> [!HINT]
>
> Want the player to choose? If you **tick** the `difficulty`{:class="block3variables"} variable, then right-click it on the stage, you can turn it into a **slider** they drag before they start.

> [!TIP]
>
> How hard a game gets, and how fast, is called its **difficulty curve**. The only way to get it right is to **play-test**: play your own game, notice when it's too easy or unfair, and adjust the numbers.
