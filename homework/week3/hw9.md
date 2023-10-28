# Homework Assignment 9

## Mina and zkApps 2

An example of sudoku implemented as zkApp (zero-knowledge smart-contract for Mina protocol) is [here](https://github.com/nlipartiia-hacken/zkapp-example-sudoku).

1. The `sudoku.ts` doesn't solve a puzzle, it allows to initialize and update the sudoku. It also implements functionality for submitting a solution, which checks if the solution is correct.

2. The method `submitSolution` checks if the solution is correct. It checks that each [raw](https://github.com/nlipartiia-hacken/zkapp-example-sudoku/blob/150d237843034b45c133755258cb53792c4c14f6/src/sudoku.ts#L64-L67), [column](https://github.com/nlipartiia-hacken/zkapp-example-sudoku/blob/150d237843034b45c133755258cb53792c4c14f6/src/sudoku.ts#L69-L72) and [3x3 square](https://github.com/nlipartiia-hacken/zkapp-example-sudoku/blob/150d237843034b45c133755258cb53792c4c14f6/src/sudoku.ts#L74-L81) contain all the numbers from 1 to 9.

3. No, if the submitted sudoku is correct and it extends the initial committed on-chain sudoku, the solution can't be rejected.

4. If the malicious prover could modify the code of zkApp deployed to the Mina, they could (for example) delete the part of the code that checks that this sudoku is a solution to the previously committed on-chain sudoku. This would allow the prover to cheat by submitting any correct sudoku, not necessarily the solution to the original one.