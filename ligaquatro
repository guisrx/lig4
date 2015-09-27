
'use strict';

function Algorithm () {
    
    var round = -1;
    var us = 'guisrx';
    var isOpening = true;
    var isOpeningLeft = true;

    this.move = function (availableColumns, gameBoard) {
        round++;

        console.log(availableColumns);
        
        // console.log("Round: " + round);
        // this.log(gameBoard);
     
        var verticalPos = this.validateMove(availableColumns, this.vertical(gameBoard));
        if (verticalPos != -1) {
            console.log("vertical: " + verticalPos);
            return verticalPos;
        }

        var openingPos = this.validateMove(availableColumns, this.opening(gameBoard));
        if (openingPos != -1) {
            console.log("opening: " + openingPos);
            return openingPos;
        }

        var horizontalPos = this.validateMove(availableColumns, this.horizontal(gameBoard));
        if (horizontalPos != -1) {
            console.log("horizontal: " + horizontalPos + " round: " + round);
            return horizontalPos;
        }

        var leftDiagonalPos = this.validateMove(availableColumns, this.leftDiagonal(gameBoard));
        if (leftDiagonalPos != -1) {
            console.log("leftDiagonalPos: " + leftDiagonalPos + " round: " + round);
            return leftDiagonalPos;
        }

        var rightDiagonalPos = this.validateMove(availableColumns, this.rightDiagonal(gameBoard));
        if (rightDiagonalPos != -1) {
            console.log("right diagonal: " + rightDiagonalPos + " round: " + round);
            return rightDiagonalPos;
        }

        var worthPlayPos = this.validateMove(availableColumns, this.worthPlay(gameBoard));
        if (worthPlayPos != -1) {
            console.log("worthPlay: " + worthPlayPos + " round: " + round);
            return worthPlayPos;
        }

        var fallbackPos = this.validateMove(availableColumns, this.fallback(gameBoard));
        if (fallbackPos != -1) {
            console.log("fallback: " + fallbackPos + " round: " + round);
            return fallbackPos;
        }

        var game = this.validateMove(availableColumns, availableColumns[round % availableColumns.length]);

        return (game != -1) ? game : availableColumns[0];
    }

    this.validateMove = function(availableColumns, move) {

        for (var i = 0; i < availableColumns.length; i++)
            if (availableColumns[i] == move)
                return move;

        console.log('invalidated: ' + move);
        return -1;
    }

    this.predictDiagonal = function(gameBoard, pos) {

        var newBoard = [];
        for (var i = 0; i < gameBoard.length; i++)
            newBoard[i] = gameBoard[i].slice();

    }

    this.worthPlay = function(gameBoard) {
    
        for (var line = 5; line >= 0; line--) {
            for (var column = 0; column < 4; column++) {
                var retColumn = -1;
/*                
                if (line = 2)
                    if(gameBoard[column][2] != gameBoard[column][3])
                        break;
*/
                // _ ! x x
                if ((!gameBoard[column][line])
                    && (!gameBoard[column +1][line])
                    && (gameBoard[column +2][line] == us)
                    && (gameBoard[column +3][line] == us))
                        retColumn = column +1;
                
                // x x ! _
                if ((gameBoard[column][line] == us)
                    && (gameBoard[column +1][line] == us)
                    && (!gameBoard[column +2][line])
                    && (!gameBoard[column +3][line]))
                        retColumn = column +2;

                // _ x ! x 
                if ((!gameBoard[column][line])
                    && (gameBoard[column +1][line] == us)
                    && (!gameBoard[column +2][line])
                    && (gameBoard[column +3][line] == us))
                        retColumn = column +2;

                // x ! x _
                if ((gameBoard[column][line] == us)
                    && (!gameBoard[column +1][line])
                    && (gameBoard[column +2][line] == us)
                    && (!gameBoard[column +3][line]))
                        retColumn = column +1;

                // _ x ! _ 
                if ((!gameBoard[column][line])
                    && (gameBoard[column +1][line] == us)
                    && (!gameBoard[column +2][line])
                    && (!gameBoard[column +3][line]))
                        retColumn = column +2;

                // _ ! x _
                if ((!gameBoard[column][line])
                    && (!gameBoard[column +1][line])
                    && (gameBoard[column +2][line] == us)
                    && (!gameBoard[column +3][line]))
                        retColumn = column +1;

                if ((retColumn != -1) && ((line == 5) || (gameBoard[retColumn][line +1])))
                    return retColumn;
            }
        }
        return -1;
    }

    this.fallback = function(gameBoard) {
    
        for (var line = 5; line >= 0; line--) {
            for (var column = 0; column < 4; column++) {
                var retColumn = -1;
                
                // _ ! _ _
                if ((!gameBoard[column][line])
                    && (!gameBoard[column +1][line])
                    && (!gameBoard[column +2][line])
                    && (!gameBoard[column +3][line]))
                        retColumn = column +1;

                if ((retColumn != -1) && ((line == 5) || (gameBoard[retColumn][line +1])))
                    return retColumn;
            }
        }
        return -1;
    }
    
    this.vertical = function(gameBoard) {
    
        for (var column = 0; column < 7; column++) {
            var count = 0;
            var last = gameBoard[column][5];    
            var line = 5;

            if (gameBoard[column][0])
                continue;

            for (; line >= 0; line--) {
                if (!gameBoard[column][line])
                    break;
                if (last == gameBoard[column][line])
                    count++;
                else {
                    count = 1;
                    last = gameBoard[column][line];
                }
            }
            if (count == 3 && line != -1)
                return column;

        }
        return -1;
    }

    this.horizontal = function(gameBoard) {
    
        for (var line = 5; line >= 0; line--) {
            for (var column = 0; column < 4; column++) {
                var retColumn = -1;

                if ((!gameBoard[column][line])
                    && (gameBoard[column +1][line])
                    && (gameBoard[column +1][line] == gameBoard[column +2][line])
                    && (gameBoard[column +2][line] == gameBoard[column +3][line]))
                        retColumn = column;

                if ((!gameBoard[column +1][line])
                    && (gameBoard[column][line])
                    && (gameBoard[column][line] == gameBoard[column +2][line])
                    && (gameBoard[column +2][line] == gameBoard[column +3][line]))
                        retColumn = column +1;

                if ((!gameBoard[column +2][line])
                    && (gameBoard[column][line])
                    && (gameBoard[column][line] == gameBoard[column +1][line])
                    && (gameBoard[column +1][line] == gameBoard[column +3][line]))
                        retColumn = column +2;

                if ((!gameBoard[column +3][line])
                    && (gameBoard[column][line])
                    && (gameBoard[column][line] == gameBoard[column +1][line])
                    && (gameBoard[column +1][line] == gameBoard[column +2][line]))
                        retColumn = column +3;

                if ((retColumn != -1) && ((line == 5) || (gameBoard[retColumn][line +1])))
                    return retColumn;
            }
        }
        return -1;
    }

    this.opening = function(gameBoard) {
    
        if (round == 0)
            if (!gameBoard[3][5])
                return 3;
            else
                isOpening = false;

        if ((round == 1) && (isOpening)) {
            if (!gameBoard[0][5] && !gameBoard[1][5] && !gameBoard[2][5])
                return 1;
                            
            if (!gameBoard[4][5] && !gameBoard[5][5] && !gameBoard[6][5]) {
                isOpeningLeft = false;
                return 5;
            }
            isOpening = false;
        }
        
        if ((round == 2) && (isOpening)) {
            if (!gameBoard[2][5] && isOpeningLeft)
                return 2;
                
            if (!gameBoard[4][5] && !isOpeningLeft)
                return 4;
                
            isOpening = false;
        }        
        
        if ((round == 3) && (isOpening)) {
            if (!gameBoard[0][5] && isOpeningLeft)
                return 0;
                
            if (!gameBoard[4][5] && isOpeningLeft)
                return 4;
            
            if (!gameBoard[6][5])
                return 6;
            
            if (!gameBoard[2][5])
                return 2;
        }
        return -1;
    }

    this.rightDiagonal = function(gameBoard) {

        for (var column = 0; column < 4; column++) {
            for (var line = 0; line < 3; line++) {

                var retColumn = -1;
                var retLine = -1;

                if ((!gameBoard[column][line])
                    && (gameBoard[column +1][line +1])
                    && (gameBoard[column +1][line +1] == gameBoard[column +2][line +2])
                    && (gameBoard[column +2][line +2] == gameBoard[column +3][line +3])){
                        retColumn = column;
                        retLine = line;
                }

                if ((!gameBoard[column +1][line +1])
                    && (gameBoard[column][line])
                    && (gameBoard[column][line] == gameBoard[column +2][line +2])
                    && (gameBoard[column +2][line +2] == gameBoard[column +3][line +3])){
                        retColumn = column +1;
                        retLine = line +1;
                }

                if ((!gameBoard[column +2][line +2])
                    && (gameBoard[column][line])
                    && (gameBoard[column][line] == gameBoard[column +1][line +1])
                    && (gameBoard[column +1][line +1] == gameBoard[column +3][line +3])){
                        retColumn = column +2;
                        retLine = line +2;
                }

                if ((!gameBoard[column +3][line +3])
                    && (gameBoard[column][line])
                    && (gameBoard[column][line] == gameBoard[column +1][line +1])
                    && (gameBoard[column +1][line +1] == gameBoard[column +2][line +2])){
                        retColumn = column +3;
                        retLine = line +3;
                }

                if ((retColumn != -1) && ((line == 5) || (gameBoard[retColumn][retLine +1])))
                    return retColumn;

            }
        }
        return -1;        
    }

    this.leftDiagonal = function(gameBoard) {

        for (var column = 0; column < 4; column++) {
            for (var line = 3; line < 6; line++) {

                var retColumn = -1;
                var retLine = -1;

                if ((!gameBoard[column][line])
                    && (gameBoard[column +1][line -1])
                    && (gameBoard[column +1][line -1] == gameBoard[column +2][line -2])
                    && (gameBoard[column +2][line -2] == gameBoard[column +3][line -3])){
                        retColumn = column;
                        retLine = line;
                }

                if ((!gameBoard[column +1][line -1])
                    && (gameBoard[column][line])
                    && (gameBoard[column][line] == gameBoard[column +2][line -2])
                    && (gameBoard[column +2][line -2] == gameBoard[column +3][line -3])){
                        retColumn = column +1;
                        retLine = line -1;
                }

                if ((!gameBoard[column +2][line -2])
                    && (gameBoard[column][line])
                    && (gameBoard[column][line] == gameBoard[column +1][line -1])
                    && (gameBoard[column +1][line -1] == gameBoard[column +3][line -3])){
                        retColumn = column +2;
                        retLine = line -2;
                }

                if ((!gameBoard[column +3][line -3])
                    && (gameBoard[column][line])
                    && (gameBoard[column][line] == gameBoard[column +1][line -1])
                    && (gameBoard[column +1][line -1] == gameBoard[column +2][line -2])){
                        retColumn = column +3;
                        retLine = line -3;
                }

                if ((retColumn != -1) && ((line == 5) || (gameBoard[retColumn][retLine +1])))
                    return retColumn;

            }
        }
        return -1;        
    }

    this.log = function(gameBoard) {
        
        for (var line = 0; line < 6; line++) {
            var boardLine = "";
            
            for (var column = 0; column < 7; column++) {
                boardLine += (!gameBoard[column][line]) ? "n" : gameBoard[column][line][0];
            }
            // console.log(boardLine);
        }
    }
    
}

