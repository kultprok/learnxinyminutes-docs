---
language: brainfuck
contributors:
    - ["Prajit Ramachandran", "http://prajitr.github.io"]
    - ["kultprok", "http://www.kulturproktologie.de"]
lang: de-de
---

Brainfuck ist eine extrem minimalistische Programmiersprache (nur 8 Befehle)
und ist turing-vollständig.

```
Alle Zeichen außer "><+-.,[]" (die Anführungszeichen ausgenommen) werden ignoriert.

Brainfuck besteht aus einem Array mit 30.000 Zellen, die auf 0 intialisiert sind, und
einem Zeiger auf die aktuelle Zelle.

Es gibt acht Befehle:
+ : Den Wert in der aktuellen Zelle um eins erhöhen.
- : Den Wert in der aktuellen Zelle um eins senken.
> : Bewegt den Datenzeiger zur nächsten Zelle (zur Rechten der aktuellen Zelle).
< : Bewegt den Datenzeiger zur vorangehenden Zelle (zur Linken der aktuellen Zelle).
. : Druckt den ASCII-Wert der aktuellen Zelle (bspw. 65 = 'A').
, : Liest ein einzelnes Eingabezeichen in die aktuelle Zelle.
[ : Wenn der Wert der aktuellen Zell null ist, springt die Ausführung zum zugehörigen ].
    Ansonsten wird der nächste Befehl ausgeführt.
] : Wenn der Wert der aktuellen Zell null ist, wird der nächste Befehl ausgeführt.
    Ansonsten geht die Ausführung zum vorangehenden [ zurück.

[ und ] bilden eine While-Schleife. Selbstverständlich müssen sie gepaart sein.

Sehen wir uns mal ein paar einfache Brainfuck-Programme an.

++++++ [ > ++++++++++ < - ] > +++++ .

This program prints out the letter 'A'. First, it increments cell #1 to 6.
Cell #1 will be used for looping. Then, it enters the loop ([) and moves
to cell #2. It increments cell #2 10 times, moves back to cell #1, and
decrements cell #1. This loop happens 6 times (it takes 6 decrements for
cell #1 to reach 0, at which point it skips to the corresponding ] and
continues on).

At this point, we're on cell #1, which has a value of 0, while cell #2 has a
value of 60. We move on cell #2, increment 5 times, for a value of 65, and then
print cell #2's value. 65 is 'A' in ASCII, so 'A' is printed to the terminal.


, [ > + < - ] > .

This program reads a character from the user input, copies the character into
another cell, and prints out the same character.

, reads in a character from the user into cell #1. Then we start a loop. Move
to cell #2, increment the value at cell #2, move back to cell #1, and decrement
the value at cell #1. This continues on until cell #1 is 0, and cell #2 holds
cell #1's old value. Because we're on cell #1 at the end of the loop, move to
cell #2, and then print out the value in ASCII.

Also keep in mind that the spaces are purely for readibility purposes. You 
could just as easily write it as

,[>+<-]>.


Try and figure out what this program does:

,>,< [ > [ >+ >+ << -] >> [- << + >>] <<< -] >>  

This program takes two numbers for input, and multiplies them.

The gist is it first reads in two inputs. Then it starts the outer loop,
conditioned on cell #1. Then it moves to cell #2, and starts the inner
loop conditioned on cell #2, incrementing cell #3. However, there comes a 
problem: at the end of the inner loop, cell #2 is zero. To solve this problem,
we also increment cell #4, and then recopy cell #4 into cell #2.
```

And that's Brainfuck. Not that hard, eh? For fun, you can write your own 
Brainfuck programs, or you can write a Brainfuck interpreter in another 
language. The interpreter is fairly simple to implement, but if you're a
masochist, trying writing a Brainfuck interpreter... in Brainfuck.
