---
layout: post
title:  "Built own computer"
date:   2018-09-27
category: tech
---

I knew for a while about a great course called [Nand 2 Tetris][nand2tetris],
and recently I committed to doing it. It's available on coursera, follow links
from [nand2tetris][nand2tetris] page.

By the end of it, I implemented a simple computer where I built the chips
for a CPU (with registers and ALU) and a RAM; and a bunch of abstractions on
top: a java like programming language - Jack, operating system libraries (for
math, for drawing pixels on the screen, for memory management etc.), a compiler,
a virtual machine and an assembler that all worked together. Eventually I was
able to play [my own chess game][jack-chess] which compiled down to machine code and ran on
the above mentioned CPU, just awesome!

I was very enthusiastic about the course and it was super fun, I learned a lot.
I hope you do to!

<br><br>

[nand2tetris]: https://www.nand2tetris.org/
[jack-chess]: https://github.com/andreip/jack-chess
