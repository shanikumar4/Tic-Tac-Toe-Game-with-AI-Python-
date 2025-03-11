
This is a Python-based Tic-Tac-Toe game where a human player (X) competes against an AI (O). The AI uses the Minimax algorithm to make optimal moves, ensuring a challenging gameplay experience.
How to Play
1.	Run the Python script.
2.	The board is displayed with empty spaces.
3.	The human player (X) makes the first move by entering the row and column numbers.
4.	The AI (O) then calculates the best possible move using the Minimax algorithm.
5.	The game continues with alternating turns until:
o	A player wins by getting three symbols in a row, column, or diagonal.
o	The board is full, resulting in a draw.
6.	The final result is displayed (Win/Loss/Draw), and the game ends.
Features
•	Fully Interactive: Players input their moves using row and column coordinates.
•	AI Opponent: The AI (O) makes the best possible move using the Minimax algorithm.
•	Board Display: The board updates dynamically after every move.
•	Win/Loss Detection: The game automatically checks for a winner after every move.
•	Draw Condition: If the board is full without a winner, the game declares a draw.
•	Input Validation: Prevents invalid moves by checking for occupied cells.
Requirements
•	Python 3.x
Running the Game
To start the game, run the following command in your terminal or command prompt:
python tic_tac_toe.py
Example Gameplay
 
 
Minimax Algorithm Explained
The Minimax algorithm is used for AI decision-making:
•	The AI evaluates all possible moves.
•	It assigns scores: +1 (AI win), -1 (Human win), 0 (Draw).
•	AI chooses the move that maximizes its chances of winning and minimizes human success.
•	This ensures that the AI never loses unless the opponent plays optimally.

