Description

This is a Python-based Tic-Tac-Toe game where you play against an AI opponent powered by the Minimax algorithm. The AI makes optimal moves, ensuring a challenging and fair gameplay experience. The game runs in the command-line interface (CLI) and follows standard Tic-Tac-Toe rules.

Features

Play against an unbeatable AI opponent.

Uses the Minimax algorithm for AI decision-making.

Simple text-based interface.

Checks for valid moves and prevents invalid inputs.

Detects wins, draws, and provides game results.

How to Play

Run the Python script.

The game board will be displayed.

You play as X, and the AI plays as O.

Enter your move by specifying the row and column numbers (e.g., 1 2 for row 1, column 2).

The AI will calculate its best move and play accordingly.

The game continues until someone wins or the board is full.

Installation

Make sure you have Python installed (Python 3.x recommended).

Download the tic_tac_toe.py script.

Run the script using:
import math  # Importing math module for handling infinity values

# Tic-Tac-Toe board (3x3 grid initialized with empty spaces)
board = [
    [' ', ' ', ' '],
    [' ', ' ', ' '],
    [' ', ' ', ' ']
]

# Function to print the board in a readable format
def print_board():
    for row in board:
        print('|'.join(row))  # Display each row with | separator
        print('-' * 5)  # Print horizontal divider between rows

# Function to check if there's a winner
def check_winner():
    # Check rows
    for row in board:
        if row[0] == row[1] == row[2] and row[0] != ' ':
            return row[0]  # Return the winning symbol (X or O)

    # Check columns
    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] and board[0][col] != ' ':
            return board[0][col]  # Return winner

    # Check diagonals
    if board[0][0] == board[1][1] == board[2][2] and board[0][0] != ' ':
        return board[0][0]  # Return winner for main diagonal
    
    if board[0][2] == board[1][1] == board[2][0] and board[0][2] != ' ':
        return board[0][2]  # Return winner for anti-diagonal

    return None  # No winner yet

# Function to check if the board is full (indicating a draw)
def is_full():
    return all(board[i][j] != ' ' for i in range(3) for j in range(3))

# Minimax algorithm (AI decision-making)
def minimax(is_maximizing):
    winner = check_winner()
    if winner == 'X':  # If human wins, return -1
        return -1
    if winner == 'O':  # If AI wins, return 1
        return 1
    if is_full():  # If it's a draw, return 0
        return 0

    if is_maximizing:  # AI's turn (O)
        best_score = -math.inf  # Start with the lowest possible score
        for i in range(3):
            for j in range(3):
                if board[i][j] == ' ':
                    board[i][j] = 'O'  # Try AI's move
                    score = minimax(False)  # Call minimax for the human's move
                    board[i][j] = ' '  # Undo move
                    best_score = max(best_score, score)  # Get the max score
        return best_score
    else:  # Human's turn (X)
        best_score = math.inf  # Start with the highest possible score
        for i in range(3):
            for j in range(3):
                if board[i][j] == ' ':
                    board[i][j] = 'X'  # Try human's move
                    score = minimax(True)  # Call minimax for AI's move
                    board[i][j] = ' '  # Undo move
                    best_score = min(best_score, score)  # Get the min score
        return best_score

# Function to determine the best move for the AI (O)
def best_move():
    best_score = -math.inf  # Start with the lowest possible score
    move = (-1, -1)  # Default move (invalid)
    for i in range(3):
        for j in range(3):
            if board[i][j] == ' ':
                board[i][j] = 'O'  # Try AI's move
                score = minimax(False)  # Evaluate the move using minimax
                board[i][j] = ' '  # Undo move
                if score > best_score:  # Update best move if score is higher
                    best_score = score
                    move = (i, j)
    return move  # Return the best move coordinates

# Main game loop
def play():
    print("Tic-Tac-Toe: You (X) vs AI (O)")
    while True:
        print_board()  # Display the board before each move

        # Human move
        x, y = map(int, input("Enter your move (row col): ").split())  # Get input
        if board[x][y] != ' ':  # Check if the move is valid
            print("Invalid move. Try again.")  # Prompt the user if the move is taken
            continue
        board[x][y] = 'X'  # Place 'X' on the board

        # Check if the human won
        if check_winner():
            print_board()
            print("You win! 🎉")  # Announce the human's victory
            break
        if is_full():  # Check for a draw
            print_board()
            print("It's a draw! 🤝")
            break

        # AI move
        i, j = best_move()  # Get the best move for AI
        board[i][j] = 'O'  # AI places 'O'
        print(f"AI plays: {i}, {j}")  # Show AI's move

        # Check if the AI won
        if check_winner():
            print_board()
            print("AI wins! 🤖")  # Announce AI's victory
            break
        if is_full():  # Check for a draw
            print_board()
            print("It's a draw! 🤝")
            break

# Run the game
play()

License

This project is open-source and free to use for learning and personal projects.

