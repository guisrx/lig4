# Lig4 (Connect Four) #

This project is an algorithm to play the lig4 game proposed by globo.com in The Developers Conference (TDC) of 2015 in Porto Alegre, Brazil.

### Problem definition ###

"Connect Four (also known as Captain's Mistress, Four Up, Plot Four, Find Four, Fourplay, Four in a Row and Four in a Line) is a two-player connection game in which the players first choose a color and then take turns dropping colored discs from the top into a seven-column, six-row vertically suspended grid. The pieces fall straight down, occupying the next available space within the column. The objective of the game is to connect four of one's own discs of the same color next to each other vertically, horizontally, or diagonally." From https://en.wikipedia.org/wiki/Connect_Four.

### Design ###

The input of the algorithm in the method 'move' is a list of available columns to be played and a matrix game board with the players names in the positions already played.

I used a hierarchy of searches for patterns in the game board in the following order:

1. **vertical**: plays in a column of 3 stones of equal color, to win or to prevent a defeat.
2. **opening**: opening strategy, plays in the middle column if possible and tries to fill 4 columns in the inverse direction of the other player first move.
3. **horizontal**: searches for a sequence of 3 stones horizontally and an open position to win or to prevent a defeat.
4. **leftDiagonal**: searches for a sequence of 3 stones int the left diagonal and an open position to win or to prevent a defeat.
5. **rightDiagonal**: searches for a sequence of 3 stones in the right diagonal and an open position to win or to prevent a defeat.
6. **worthPlay**: searches for a position where is possible to form a winning sequence with the stones found in the game board.
7. **fallback**: plays in a position with three more open spaces or where is possible.

### To Do ###

The game was solved by James Dow Allen (October 1, 1988), so a winning strategy should be implemented.
