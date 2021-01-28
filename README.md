# Rubik's Cube Solution

[LannyRipple](https://gist.github.com/LannyRipple)'s preferred algorithms for solving the cube.  Basically
a 4-Look CFOP plus some bonus material.

See

   * https://cubefreak.weebly.com/2-look-oll.html
   * https://cubefreak.weebly.com/2-look-pll.html
   * https://www.youtube.com/watch?v=DTYvklyOpVM
   * https://www.youtube.com/watch?v=S61q3FYVFis

Table Of Contents
=================
<!--ts-->
   * [Rubik's Cube Solution](#rubiks-cube-solution)
   * [Table Of Contents](#table-of-contents)
      * [Notation](#notation)
      * [Overview](#overview)
         * [Triggers](#triggers)
      * [OLL Edges](#oll-edges)
         * [Line](#line)
         * [L](#l)
         * [Dot](#dot)
      * [OLL Corners (w/ probability)](#oll-corners-w-probability)
         * [Sune (4/17)](#sune-417)
         * [Anti-Sune (4/17)](#anti-sune-417)
         * [Pi (2/17)](#pi-217)
         * [Headlights (2/17)](#headlights-217)
         * [Chameleon (2/17)](#chameleon-217)
         * [Bowtie (2/17)](#bowtie-217)
         * [H  (1/17)](#h--117)
         * [Just Sune](#just-sune)
      * [2-Look PLL](#2-look-pll)
         * [A-Perm CW](#a-perm-cw)
         * [E-Perm](#e-perm)
         * [Three Edge CW](#three-edge-cw)
         * [Three Edge CCW](#three-edge-ccw)
         * [Swap Opposite Edges](#swap-opposite-edges)
         * [Swap Adjacent Edges](#swap-adjacent-edges)
      * [Rotate Center Face](#rotate-center-face)
      * [M Slice Algorithms](#m-slice-algorithms)
         * [Inverted Opposite Edges](#inverted-opposite-edges)
         * [Three Edge Cycle](#three-edge-cycle)
         * [Opposite Color H](#opposite-color-h)

<!-- Added by: lanny, at: 2018-09-03T00:38-05:00 -->

<!--te-->

## Notation

Sym | Meaning
--- | ---
U | Up
D | Down
L | Left
R | Right
F | Front
B | Back

CW moves viewing the face are listed directly while
CCW face rotations are listed with a "'".  E.g. R'
Be careful about D and D'.  Rotating in direction of
right thumb if right palm is on the face is CW.

A "s" postfix means moving the face and the far face
in the same direction.  So Rs means (R L').  A "a"
postfix means moving the face and the far face in
opposite directions.  So Ra means (R L).  A lot of
algorithms seem to prefer listing the far face as
s rather than s'.  E.g., Bs rather than Fs'.

Sym | Name | Meaning
---|---|---
M | Middle | Layer between L and R
E | Equator | Layer between U and D
S | Standing | Layer between F and B

Rotating a face twice uses a "2".  E.g., R2 (or R2')

A full cube rotation is noted as

Sym | Meaning
--- | ---
x | Rotate about R
y | Rotate about U
z | rotate about F

A lower case face, e.g., "r", means to rotate 2 layers.

## Overview

1. Cross
1. F2L
1. OLL Edges
1. OLL Corners
1. 2-Look PLL
1. (Bonus) Rotate Center Face

I'm not going to detail Cross and F2L*.  Unless specified
the face opposite the cross is UP.

* In F2L if you see an edge for which the non-top face matches the L or R center
then the edge is oriented and can be placed without a cube rotation and using only
turns of the L, R, or U face.  See https://www.youtube.com/watch?v=za9RvM1bS0k

Sym | Meaning
--- | ---
\*        | a face color
o        | an opposite side face color
X        | a don't know/don't care color
1,2,...  | face color in given direction

### Triggers

  * Sexy Move: R U R' U'
  * Sledgehammer: R' F R F'

Sledgehammer finds a lot of use in F2L.

  * Undo: U R U' R'
  * HedgeSlammer: F R' F' R

## OLL Edges

### Line

    XXX
    ***         F (R U R' U') F'
    XXX

### L

    XXX
    X**         f (R U R' U') f'
    X*X

### Dot

    XXX
    X*X         F (R U R' U') F' f (R U R' U') f'
    XXX         Line then L from above.

## OLL Corners (w/ probability)

### Sune (4/17)

 Twist 3 corners CW.

    1
    X*X2
    ***         (R U R') U (R U2 R')
    **X
      3

A note on what Sune is doing.  It pulls out the F/R F2L,
moves them CW to L side of U, then (R U2 R') drops it back
into place.  In doing so the 3 corners get rotated.

### Anti-Sune (4/17)

 Twist 3 corners CCW.

       3
     **X
     ***        (R' U' R) U' (R' U2 R)
     X*X2
     1

Note how you are doing a Sune on the B/R F2L with
a CCW progression.

### Pi (2/17)

       3
    1X*X
     ***        f (R U R' U') f' F (R U R' U') F'
    2X*X        L then Line from solving cross.
       4

### Headlights (2/17)

     ***
     ***        R2' D (R' U2 R) D' (R' U2 R')
     X*X
     1 2

### Chameleon (2/17)

     1
     X**
     ***        (r U R' U') (r' F R F')
     X**
     2

### Bowtie (2/17)

    1X**
     ***        F' (r U R' U') (r' F R)
     **X
       2

### H  (1/17)

     1 2
     X*X
     ***        F (R U R' U')3 F'
     X*X
     3 4

### Just Sune

Note that the non-Sune cases can be reduced to a double application
of Sune and Anti-Sune.  The two open position cubes can be solved with
Sune + Anti-Sune while the four open position cubes can be solved with
a double Sune application.

            1
    ***     X**     **X2
    ***     ***     ***     Solved with Sune + Anti-Sune.
    X*X     X**     X**     Basically: Hold onto a CCW corner.
    1 2     2       1

       3
    1X*X    1X*X3           Solved with Sune + Sune.
     ***     ***            Basically: Hold onto a CW corner.
    2X*X    2X*X4
       4


## 2-Look PLL

If corners are correct skip to 2.

1. Find "headlights".  A pair of the same color.  Move these to
B face (LL is still U) and run (the x moves U to B)

        A-Perm CCW:     x [(R' U R') D2] [(R U' R') D2] R2

    If no headlights found run A-Perm CCW anyway and then go back
    to 1.

    To solve directly you can run the following

        E-Perm:         x' [(R U' R') D (R U R')] D2 [(L' U L) D (L' U' L)]

    or alternately

        Y-PERM:         (F R U') (R' U' R U) (R' F') (R U R' U') (R' F R F')

1. One of the following is now garaunteed to apply.

### A-Perm CW

    1*2     3*1
    *** ==> ***     x [(R' U R') D2] [(R U' R') D2] R2
    **3     **2

### E-Perm

    1*3     2*4
    *** ==> ***     x' [(R U' R') D (R U R')] D2 [(L' U L) D (L' U' L)]
    2*4     1*3

### Three Edge CCW

Peek the F/R corner and ask if F needs to go to R?

    ***     ***
    3*2 ==> 2*1     (R U') (R U) (R U) (R U') (R' U') R2
    *1*     *3*

### Three Edge CW

    ***     ***
    2*3 ==> 1*2     (L' U) (L' U') (L' U') (L' U) (L U) L
    *1*     *3*

### Swap Opposite Edges

    *2*     *1*
    4*3 ==> 3*4     (M2 U M2) U2 (M2 U M2)
    *1*     *2*

### Swap Adjacent Edges

I prefer

    *2*     *1*
    1*4 ==> 2*3     (M2 U M2' U') E2 M' E2 M'
    *3*     *4*

to the recommended algorithm

    *2*     *1*
    1*4 ==> 2*3     (M2' U M2') U M' (U2 M2' U2) M' U2
    *3*     *4*

## Rotate Center Tile

To rotate a center tile place face with tile as L face
and run

    (M' E' M) U (M' E M) U'

which will rotate L and U centers by 90 degrees CW.

To rotate a single middle center by 180 degrees run

    (U R L U2 R' L')2

## M Slice Algorithms

I first learned to solve a cube by solving bottom and top
layers and then fixing the middle.  I still bump into the
need for middle algorithms so here are a few.

### Inverted Opposite Edges

An oldy but goody.  Here 1 and 2 are the color of the
face they are attached to.

    *1*
    ***             (M U' M U' M U2) (M' U M' U M' U2)
    *2*

### Three Edge Cycle

Hard to describe.  Two edges have a proper face color and
are out of position by a single side.  The third comes from
the other side of the cube.

I imagine the very odd was is "the rock" and the other
pieces are falling onto it.  The rock is M/B and other
edges are in U.

    M U2 M'

### Opposite Color H

    *o*
    ***             D2 M2 D2 M2
    *o*

__END__
