# Tic---Tac-game
childhood Tic-Tac game java code so that you can play easily 

```java
import java.util.Scanner;

public class TicTacToe {

    static char[] board = {
        '1', '2', '3',
        '4', '5', '6',
        '7', '8', '9'
    };

    static Scanner sc = new Scanner(System.in);

    // Display the game board
    static void displayBoard() {
        System.out.println();
        System.out.println(" " + board[0] + " | " + board[1] + " | " + board[2]);
        System.out.println("---+---+---");
        System.out.println(" " + board[3] + " | " + board[4] + " | " + board[5]);
        System.out.println("---+---+---");
        System.out.println(" " + board[6] + " | " + board[7] + " | " + board[8]);
        System.out.println();
    }

    // Check if a player has won
    static boolean checkWinner(char player) {
        int[][] winningPositions = {
            {0, 1, 2},
            {3, 4, 5},
            {6, 7, 8},
            {0, 3, 6},
            {1, 4, 7},
            {2, 5, 8},
            {0, 4, 8},
            {2, 4, 6}
        };

        for (int[] position : winningPositions) {
            if (board[position[0]] == player &&
                board[position[1]] == player &&
                board[position[2]] == player) {
                return true;
            }
        }

        return false;
    }

    // Check if the board is full
    static boolean isBoardFull() {
        for (char space : board) {
            if (space != 'X' && space != 'O') {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {

        char player = 'X';

        System.out.println("===== TIC-TAC-TOE =====");
        System.out.println("Player 1 = X");
        System.out.println("Player 2 = O");

        while (true) {

            displayBoard();

            System.out.print("Player " + player + ", choose a position (1-9): ");
            int position = sc.nextInt();

            // Check if position is valid
            if (position < 1 || position > 9) {
                System.out.println("Invalid position! Choose between 1 and 9.");
                continue;
            }

            // Check if position is already taken
            if (board[position - 1] == 'X' || board[position - 1] == 'O') {
                System.out.println("That position is already taken!");
                continue;
            }

            // Place X or O
            board[position - 1] = player;

            // Check winner
            if (checkWinner(player)) {
                displayBoard();
                System.out.println("🎉 Player " + player + " wins!");
                break;
            }

            // Check draw
            if (isBoardFull()) {
                displayBoard();
                System.out.println("It's a draw!");
                break;
            }

            // Change player
            if (player == 'X') {
                player = 'O';
            } else {
                player = 'X';
            }
        }

        sc.close();
    }
}
```
