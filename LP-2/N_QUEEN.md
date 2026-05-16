
Practical4_NQueens

Implement a solution for a Constraint Satisfaction Problem using Branch and Bound and 
Backtracking for n-queens problem or a graph coloring problem. 

Code:

# ---------------------------------------------------
# N-Queens Problem using
# Backtracking + Branch and Bound Technique
# ---------------------------------------------------

# Function to print chessboard
def print_board(board):

    for row in board:
        print(" ".join(row))

    print()


# ---------------------------------------------------
# Function to check whether queen can be placed safely
# ---------------------------------------------------
def is_safe(board, row, col, n):

    # ---------- Branch and Bound ----------
    # Check left side of current row
    for j in range(col):

        if board[row][j] == 'Q':
            return False

    # ---------- Branch and Bound ----------
    # Check upper-left diagonal
    i = row
    j = col

    while i >= 0 and j >= 0:

        if board[i][j] == 'Q':
            return False

        i -= 1
        j -= 1

    # ---------- Branch and Bound ----------
    # Check lower-left diagonal
    i = row
    j = col

    while i < n and j >= 0:

        if board[i][j] == 'Q':
            return False

        i += 1
        j -= 1

    # Safe position found
    return True


# ---------------------------------------------------
# Recursive function to solve N-Queens problem
# ---------------------------------------------------
def solve_nq_util(board, col, n):

    # Base Condition
    # If all queens are placed successfully
    if col >= n:
        return True

    # Try placing queen in every row
    for i in range(n):

        # ---------- Branch and Bound ----------
        # Continue only if position is safe
        if is_safe(board, i, col, n):

            # Place queen
            board[i][col] = 'Q'

            # ---------- Recursion / Branch ----------
            # Move to next column
            if solve_nq_util(board, col + 1, n):
                return True

            # ---------- Backtracking ----------
            # Remove queen if solution fails
            board[i][col] = '.'

    # No valid position found
    return False


# ---------------------------------------------------
# Main Function
# ---------------------------------------------------
def solve_n_queens(n):

    # Create empty chessboard
    board = [['.' for _ in range(n)] for _ in range(n)]

    # Solve problem starting from column 0
    if solve_nq_util(board, 0, n):

        print("\nOne Solution Found:\n")

        print_board(board)

        print("Search completed using Backtracking and Branch and Bound")

    else:

        print("No solution exists")


# ---------------------------------------------------
# Driver Code
# ---------------------------------------------------

# Take user input for number of queens
n = int(input("Enter value of N: "))

# Solve N-Queens Problem
solve_n_queens(n)
