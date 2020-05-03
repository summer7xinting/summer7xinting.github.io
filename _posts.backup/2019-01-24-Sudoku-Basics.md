---
layout: post
title:  "Sudoku Basics"
permalink: sudoku-basics
---

## Goal
* Complete a 9x9 grid where every row, every column, every box contains nine different numbers. 
* Note that a true Sudoku has only one solution. 

## Technique
* **Cross-Hatching**: take number "1" as an example
    * See the Sudoku as a 3x3 grid of boxes where each box has 3 "1"s in different rows/columns. For each row/column of "boxes", if two "1"s are settled, the other "1" has to appear in the remaining row/column. Based on column/row information, (partially) locate the "1". If only one "1" is settled, no move should be made.  
    * Use this technique for each number in each row/column of boxes -> mark the dual possibility along the way **AND** repeat the process whenever you have a good amount of more information. 
* **Elimination**: when the row/column/box has no more than 3 open spots
    * Find the remaining numbers and eliminate the impossibles using other row/column
    * 
* **Non-overlapping Elimination**: when you have no clue where to start
    * Find the row/column/box that has the maximum non-overlapping numbers: if they encompass 8 numbers -> their intersection is settled using elimination **OR** if they encompass 7 numbers -> a good place to start in a hard puzzle: try both entry point and one of them will lead to a dead end.
    * 
* Only fill in when **sure**: 
    * For an easy puzzle, the answer is almost obvious, **BUT** for a hard one, there are often more than one possibility that could potentially satisfy the rules. Leave marks about the narrowed-down guess without filling it in since one error in the middle steps renders any work that comes after it useless. 
    * Number the steps if possible so it's easier to backtrace your error. 

## Check
* If the Sudoku is not complete and already has conflicts (same number in same row/column/box): **Either** this is a dead end for the assumption you made -> Start with another assumption **OR** you have made a mistake -> backtrace/forwardtrace step-by-step to the last "good" status. 
    * To backtrace: number the steps you made and go back to the mistake
    * To forwardtrace: start from the beginning and circle all "good" points until you reach the mistake
* If the Sudoku is complete: check every row/column/box to confirm the solution.

## Inspiration From Others
* Amazing medium/hard-level technique [here](https://www.youtube.com/watch?v=sIlnGUejg7Y)
* 