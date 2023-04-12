**Question** ([link](https://py.checkio.org/en/mission/x-o-referee/))


Tic-Tac-Toe, sometimes also known as Xs and Os, is a game for two players (X and O) who take turns marking the spaces in a 3×3 grid. The player who succeeds in placing three respective marks in a horizontal, vertical, or diagonal rows (NW-SE and NE-SW) wins the game.

But we will not be playing this game. You will be the referee for this games results. You are given a result of a game and you must determine if the game ends in a win or a draw as well as who will be the winner. Make sure to return "X" if the X-player wins and "O" if the O-player wins. If the game is a draw, return "D".

x-o-referee

A game's result is presented as a list of strings, where "X" and "O" are players' marks and "." is the empty cell.

Input: A game result as list of strings (unicode).

Output: "X", "O" or "D" as a string.

Examples:

```python
assert checkio(["X.O", "XX.", "XOO"]) == "X"
assert checkio(["OO.", "XOX", "XOX"]) == "O"
assert checkio(["OOX", "XXO", "OXX"]) == "D"
assert checkio(["O.X", "XX.", "XOO"]) == "X"

```

**My Solution**

```python
from typing import List


def checkio(gr: List[str]) -> str:
    columns = [gr[0][0] + gr[1][0] + gr[2][0], gr[0][1] + gr[1][1] + gr[2][1], gr[0][2] + gr[1][2] + gr[2][2]]
    angles = [gr[0][0] + gr[1][1] + gr[2][2], gr[2][0] + gr[1][1] + gr[0][2]]

    for triplet in gr + columns + angles:
        if triplet[0] == triplet[1] == triplet[2] != '.':
            return triplet[0]

    return "D"

if __name__ == "__main__":
    print("Example:")
    print(checkio(["X.O", "XX.", "XOO"]))

    # These "asserts" using only for self-checking and not necessary for auto-testing
    assert checkio(["X.O", "XX.", "XOO"]) == "X", "X wins"
    assert checkio(["OO.", "XOX", "XOX"]) == "O", "O wins"
    assert checkio(["OOX", "XXO", "OXX"]) == "D", "Draw"
    assert checkio(["O.X", "XX.", "XOO"]) == "X", "X wins again"
    print("Coding complete? Click 'Check' to review your tests and earn cool rewards!")

