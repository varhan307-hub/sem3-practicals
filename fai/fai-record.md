PERI INSTITUTE OF TECHNOLOGY
DEPARTMENT OF ARTIFICIAL INTELLIGENCE AND DATA SCIENCE
FUNDAMENTALS OF ARTIFICAL INTELLIGENCE
NAME :
REGISTER NO :
YEAR/SEMESTER : II Year / III Semester
1

FUNDAMENTALS OF ARTIFICAL INTELLIGENCE
COURSE OBJECTIVES:
❖ ∙ To design and implement search strategies
❖ ∙ To implement game playing techniques
❖ ∙ To implement CSP techniques
❖ ∙ To develop systems with logical reasoning
❖ ∙ To develop systems with probabilistic reasoning
LIST OF EXPERIMENTS
1. Implement basic search strategies – 8-Puzzle, 8 - Queens problem, Cryptarithmetic.
2. Implement A* and memory bounded A* algorithms
3. Implement Minimax algorithm for game playing (Alpha-Beta pruning)
4. Solve constraint satisfaction problems
5. Implement propositional model checking algorithms
6. Implement forward chaining, backward chaining, and resolution strategies
7. Build naïve Bayes models
8. Implement Bayesian networks and perform inferences
9. Mini-Project
OUTCOMES:
At the end of this course, the students will be able to:
CO1: Design and implement search strategies
CO2: Implement game playing and CSP techniques
CO3: Develop logical reasoning systems
CO4: Develop probabilistic reasoning systems
2

|              |                         | PAGE  | DATE OF     | MARK  |            |
| ------------ | ----------------------- | ----- | ----------- | ----- | ---------- |
| S.No.  DATE  | NAME OF THE EXPERIMENT  |       |             |       | SIGNATURE  |
|              |                         | NO    | SUBMISSION  | (10)  |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |
|              |                         |       |             |       |            |

3

EX Implement basic search strategies – 8-Puzzle
NO:1a
Aim:
To implement an basic search starategies like 8-puzzle.
Algorithm for 8-Puzzle:
1.Define the Problem:
∙ Identify the initial state of the puzzle.
∙ Define the goal state.
2.Generate Initial Node:
∙ Create a node representing the initial state.
∙ Initialize other necessary information, such as cost and heuristic.
3.Create Frontier:
∙ Initialize a frontier (open list) with the initial node.
4.Create Explored Set:
∙ Initialize an explored set (closed list) to keep track of visited states.
5.While Frontier is Not Empty:
∙ Pop a node from the frontier.
∙ Check if the node represents the goal state. If yes, return the solution.
∙ Otherwise, expand the node by generating its neighbors.
6.Expand Node:
∙ For each valid action, generate a new state by applying the action.
∙ Create a new node for the new state.
∙ Calculate the cost and heuristic for the new node.
∙ Add the new node to the frontier if it's not in the explored set.
7.Update Explored Set:
∙ Add the current node's state to the explored set.
8.Return Failure:
∙ If the frontier is empty and the goal state is not reached, return failure (no solution).
9.Return Solution Path:
∙ If the goal state is reached, return the solution path from the initial
state to the goal state.
4

PROGRAM:
import heapq
import copy
class PuzzleNode:
def __init__(self, state, parent=None, action=None, cost=0):
self.state = state
self.parent = parent
self.action = action
self.cost = cost
self.heuristic = self.calculate_heuristic()
def __lt__(self, other):
return (self.cost + self.heuristic) < (other.cost + other.heuristic)
def calculate_heuristic(self):
# A simple heuristic function: Manhattan distance
goal_state = [[1, 2, 3], [4, 5, 6], [7, 8, 0]]
heuristic = 0
for i in range(3):
for j in range(3):
if self.state[i][j] != 0:
goal_i, goal_j = divmod(self.state[i][j] - 1, 3)
heuristic += abs(i - goal_i) + abs(j - goal_j)
return heuristic
def get_blank_position(state):
5

for i in range(3):
for j in range(3):
if state[i][j] == 0:
return i, j
def get_neighbors(node):
i, j = get_blank_position(node.state)
neighbors = []
for action in [(0, 1), (0, -1), (1, 0), (-1, 0)]:
new_i, new_j = i + action[0], j + action[1]
if 0 <= new_i < 3 and 0 <= new_j < 3:
new_state = copy.deepcopy(node.state)
new_state[i][j], new_state[new_i][new_j] = new_state[new_i][new_j], new_state[i][j]
neighbors.append(PuzzleNode(new_state, node, action, node.cost + 1))
return neighbors
def a_star(initial_state):
start_node = PuzzleNode(initial_state)
frontier = [start_node]
explored = set()
while frontier:
node = heapq.heappop(frontier)
if node.state == [[1, 2, 3], [4, 5, 6], [7, 8, 0]]:
return get_solution_path(node)
explored.add(tuple(map(tuple, node.state)))
for neighbor in get_neighbors(node):
if tuple(map(tuple, neighbor.state)) not in explored:
heapq.heappush(frontier, neighbor)
return None
def get_solution_path(node):
path = []
6

while node.parent:
path.append((node.state, node.action))
node = node.parent
path.append((node.state, node.action))
path.reverse()
return path
def print_solution_path(path):
for i, (state, action) in enumerate(path):
print(f"Step {i + 1}:")
print_state(state)
if action:
print(f"Action: Move {state[action[0]][action[1]]} {action_direction(action)}\n")
def action_direction(action):
if action == (0, 1):
return "right"
elif action == (0, -1):
return "left"
elif action == (1, 0):
return "down"
elif action == (-1, 0):
return "up"
def print_state(state):
for row in state:
print(row)
print()
if __name__ == "__main__":
initial_state = [[1, 2, 3], [4, 0, 5], [7, 8, 6]]
print("Initial State:")
print_state(initial_state)
7

solution_path = a_star(initial_state)
if solution_path:
print("Solution Path:")
print_solution_path(solution_path)
else:
print("No solution found.")
OUTPUT:
Initial State:
[1, 2, 3]
[4, 0, 5]
[7, 8, 6]
Solution Path:
Step 1:
[1, 2, 3]
[4, 0, 5]
[7, 8, 6]
Step 2:
[1, 2, 3]
[4, 5, 0]
[7, 8, 6]
Action: Move 2 right
Step 3:
[1, 2, 3]
[4, 5, 6]
[7, 8, 0]
Action: Move 4 down
>>>
RESULT:
Thus the above program was implemented and executed successfully.
8

EX Implement basic search strategies – 8 - Queens problem
NO:1b
Aim:
To implement an basic search starategies like 8- Queens problem.
Algorithm for 8-Queens Problem:
1.Define the Problem:
∙ Identify the constraints of the 8-Queens problem.
∙ Define the goal of placing eight queens without any conflicts.
2.Generate Initial State:
∙ Create an empty 8x8 chessboard.
∙ Create a Search Space:
∙ Define the search space representing all possible configurations of
queens on the chessboard. 3.Define State Transition Operators:
∙ Define operators that represent valid moves or placements of queens.
4.Define Goal State:
∙ Specify the conditions for a solution, i.e., a state where eight queens are placed
without any conflicts.
5.Select a Search Algorithm:
∙ Choose a search algorithm to explore the search space systematically.
∙ Common algorithms include depth-first search, breadth-first search, or backtracking.
6.Implement the Search Algorithm:
∙ Implement the selected search algorithm to explore the state space and
find a valid solution. 7.Check Constraints:
∙ During the search, ensure that each state adheres to the constraints of the
problem (no conflicts). 8.Backtrack if Necessary:
∙ If a conflict is detected, backtrack to the previous state and try alternative moves.
9.Return Solution:
∙ Once a state is found where eight queens are placed without conflicts,
return it as the solution.
PROGRAM:
class EightQueensProblem:
def __init__(self, size=8):
9

self.size = size
self.solution = [None] * size
def is_safe(self, row, col):
for prev_row in range(row):
prev_col = self.solution[prev_row]
if prev_col == col or \
prev_col - prev_row == col - row or \
prev_col + prev_row == col + row:
return False
return True
def solve_queens(self, row):
if row == self.size:
return True
for col in range(self.size):
if self.is_safe(row, col):
self.solution[row] = col
if self.solve_queens(row + 1):
return True
self.solution[row] = None
return False
def print_solution(self):
for row in range(self.size):
line = ""
for col in range(self.size):
if col == self.solution[row]:
line += "Q "
else:
line += ". "
print(line.strip())
if __name__ == "__main__":
queens_problem = EightQueensProblem()
if queens_problem.solve_queens(0):
print("Solution Found:")
queens_problem.print_solution()
else:
print("No solution exists.")
10

OUTPUT:
Solution Found:
Q . . . . . . .
. . . . Q . . .
. . . . . . . Q
. . . . . Q . .
. . Q . . . . .
. . . . . . Q .
. Q . . . . . .
. . . Q . . . .
>
RESULT:
Thus the above program was implemented and executed successfully.
11

EX Implement basic search strategies – Cryptarithmetic
NO:1c
Aim:
To implement an basic search starategies like Cryptarithmetic.
Algorithm for Cryptarithmetic:
1.Define the Problem:
∙ Identify the given cryptarithmetic problem, including the arithmetic
expression and any constraints.
2.Generate Initial State:
∙ Create an initial state with variable assignments (digits) set to None.
3.Create a Search Space:
∙ Define the search space representing all possible digit assignments to letters.
4.Define State Transition Operators:
∙ Define operators that represent valid changes to the current state, such as
assigning a digit to a letter.
5.Define Goal State:
∙ Specify the conditions for a solution, i.e., a state where the arithmetic expression is
satisfied with valid digit assignments.
6.Select a Search Algorithm:
∙ Choose a search algorithm suitable for exploring the state space efficiently.
Backtracking is commonly used for Cryptarithmetic problems.
7.Implement the Search Algorithm:
∙ Implement the chosen search algorithm to explore the state space and
find a valid solution. 8.Check Constraints:
∙ During the search, ensure that each state adheres to the constraints of the
cryptarithmetic problem (unique digit assignments).
9.Backtrack if Necessary:
∙ If a conflict is detected or if a partial assignment cannot lead to a valid solution,
backtrack to the previous state and try alternative assignments.
10.Return Solution:
∙ Once a valid digit assignment is found that satisfies the cryptarithmetic problem,
return it as the solution.
12

PROGRAM:
def is_valid(assignment, word, mapping):
return sum(mapping[letter] for letter in word[:-1]) % 10 == mapping[word[-1]]
def solve_cryptarithmetic(puzzle):
letters = set("".join(puzzle))
if len(letters) > 10:
print("Invalid puzzle. Too many unique letters.")
return None
def backtrack(mapping, index):
if index == len(letters):
return True
letter = list(letters)[index]
for digit in range(10):
if digit not in mapping.values():
mapping[letter] = digit
if all(is_valid(mapping, word, mapping) for word in puzzle):
if backtrack(mapping, index + 1):
return True
mapping[letter] = None
return False
initial_mapping = {letter: None for letter in letters}
if backtrack(initial_mapping, 0):
return initial_mapping
else:
print("No solution found.")
return None
def print_solution(mapping, puzzle):
for word in puzzle:
print(" + ".join(str(mapping[letter]) for letter in word[:-1]), end=" = ")
print(mapping[word[-1]])
if __name__ == "__main__":
puzzle = ["SEND", "MORE", "MONEY"]
print("Cryptarithmetic Puzzle:")
for word in puzzle:
print(word, end=" ")
print()
solution = solve_cryptarithmetic(puzzle)
13

if solution:
print("\nSolution:")
print_solution(solution, puzzle)
else:
print("\nNo solution found.")
OUTPUT:
Cryptarithmetic Puzzle:
SEND MORE MONEY
RESULT:
Thus the above program was implemented and executed successfully.
14

EX Implement A* algorithms
NO:2a
Aim:
To implement an basic search starategies like Implement A* search algorithm.
Algorithm for A* search algorithm:
1.Initialize Open and Closed Sets:
∙ Create an open set to store nodes to be evaluated.
∙ Create a closed set to store nodes that have already been evaluated.
2.Initialize Start Node:
∙ Add the start node to the open set.
3.While Open Set is Not Empty:
∙ Pop the node with the lowest total cost (actual cost + heuristic) from the open set.
∙ If the popped node is the goal, reconstruct and return the solution path.
4.Generate Successors:
∙ For each successor of the current node:
∙ Calculate the actual cost from the start node.
∙ Calculate the heuristic value from the successor to the goal.
∙ Calculate the total cost as the sum of the actual cost and heuristic.
∙ If the successor is not in the open set or has a lower total cost, update its cost
and add it to the open set.
5.Update Closed Set:
∙ Add the current node to the closed set.
6.Return Failure:
∙ If the open set is empty and the goal has not been reached, return
failure (no solution). PROGRAM:
import heapq
def heuristic(node, goal):
# Euclidean distance heuristic
return ((node[0] - goal[0]) ** 2 + (node[1] - goal[1]) ** 2) ** 0.5
def astar_search(start, goal, graph):
open_set = [(0, start)]
closed_set = set()
came_from = {}
15

g_score = {start: 0}
f_score = {start: heuristic(start, goal)
}
while open_set:
current_f, current = heapq.heappop(open_set)
if current == goal:
path = reconstruct_path(came_from, current)
return path
closed_set.add(current)
for neighbor in graph[current]:
if neighbor in closed_set:
continue
tentative_g = g_score[current] + 1
if neighbor not in [item[1] for item in open_set] or tentative_g < g_score[neighbor]:
came_from[neighbor] = current
g_score[neighbor] = tentative_g
f_score[neighbor] = tentative_g + heuristic(neighbor, goal)
heapq.heappush(open_set, (f_score[neighbor], neighbor))
return None
def reconstruct_path(came_from, current):
path = [current]
while current in came_from:
current = came_from[current]
path.append(current)
return path[::-1]
if __name__ == "__main__":
# Example usage
graph = {
(0, 0): [(1, 0), (0, 1)],
(1, 0): [(0, 0), (2, 0)],
(0, 1): [(0, 0), (1, 1), (0, 2)],
(1, 1): [(0, 1), (2, 1)],
(0, 2): [(0, 1), (1, 2)],
(2, 0): [(1, 0), (2, 1)],
(2, 1): [(1, 1), (2, 0), (2, 2)],
(1, 2): [(0, 2), (2, 2)],
(2, 2): [(1, 2), (2, 1)]
}
start_node = (0, 0)
goal_node = (2, 2)
result = astar_search(start_node, goal_node, graph)
16

if result:
print(f"Shortest Path from {start_node} to {goal_node}: {result}")
else:
print("No path found.")
OUTPUT:
Shortest Path from (0, 0) to (2, 2): [(0, 0), (0, 1), (0, 2), (1, 2), (2, 2)]
>
RESULT:
Thus the above program was implemented and executed successfully.
17

EX
NO:2a Implement A* and memory bounded A* algorithms
Aim:
To implement an basic search strategies memory bounded A* search algorithm.
Algorithm for memory bounded A* search algorithm:
Algorithm for A Search:*
1.Initialize Open and Closed Sets:
∙ Create an open set to store nodes to be evaluated.
∙ Create a closed set to store nodes that have already been evaluated.
2.Initialize Start Node:
∙ Add the start node to the open set.
3.While Open Set is Not Empty:
∙ Pop the node with the lowest total cost (actual cost + heuristic) from the open set.
∙ If the popped node is the goal, reconstruct and return the solution path.
4.Generate Successors:
5.For each successor of the current node:
∙ Calculate the actual cost from the start node.
∙ Calculate the heuristic value from the successor to the goal.
∙ Calculate the total cost as the sum of the actual cost and heuristic.
∙ If the successor is not in the open set or has a lower total cost, update its cost and
add it to the open set.
6.Update Closed Set:
∙ Add the current node to the closed set.
7.Return Failure:
∙ If the open set is empty and the goal has not been reached, return
failure (no solution).
18

PROGRAM:
import heapq
def heuristic(node, goal):
return abs(node[0] - goal[0]) + abs(node[1] - goal[1])
def memory_bounded_astar(start, goal, graph, memory_limit):
open_set = [(0, start)]
closed_set = set()
came_from = {}
g_score = {start: 0}
f_score = {start: heuristic(start, goal)}
while open_set:
current_f, current = heapq.heappop(open_set)
if current == goal:
path = reconstruct_path(came_from, current)
return path
closed_set.add(current)
for neighbor in graph[current]:
if neighbor in closed_set:
continue
tentative_g = g_score[current] + 1
if neighbor not in [item[1] for item in open_set] or tentative_g < g_score[neighbor]:
came_from[neighbor] = current
g_score[neighbor] = tentative_g
f_score[neighbor] = tentative_g + heuristic(neighbor, goal)
heapq.heappush(open_set, (f_score[neighbor], neighbor))
# Prune nodes based on memory limit
if len(open_set) > memory_limit:
open_set = open_set[:memory_limit]
return None
def reconstruct_path(came_from, current):
path = [current]
while current in came_from:
current = came_from[current]
path.append(current)
return path[::-1]
if __name__ == "__main__":
# Example usage
19

graph = {
(0, 0): [(1, 0), (0, 1)],
(1, 0): [(0, 0), (2, 0)],
(0, 1): [(0, 0), (1, 1), (0, 2)],
(1, 1): [(0, 1), (2, 1)],
(0, 2): [(0, 1), (1, 2)],
(2, 0): [(1, 0), (2, 1)],
(2, 1): [(1, 1), (2, 0), (2, 2)],
(1, 2): [(0, 2), (2, 2)],
(2, 2): [(1, 2), (2, 1)]
}
start_node = (0, 0)
goal_node = (2, 2)
memory_limit = 5 # Set the memory limit
result = memory_bounded_astar(start_node, goal_node, graph, memory_limit)
if result:
print(f"Shortest Path from {start_node} to {goal_node}: {result}")
else:
print("No path found.")
OUTPUT:
Shortest Path from (0, 0) to (2, 2): [(0, 0), (0, 1), (0, 2), (1, 2), (2, 2)]
>
RESULT:
Thus the above program was implemented and executed successfully.
20

EX Implement Minimax algorithm for game playing (Alpha-Beta pruning)
NO:3
Aim:
To implement an basic search starategies memory bounded A* search algorithm.
Algorithm:
Minimax Function with Alpha-Beta Pruning:
Function minimax(node, depth, alpha, beta, maximizingPlayer):
If depth == 0 or node is a terminal node:
Return the utility value of the node.
If maximizingPlayer is true:
Initialize v to negative infinity.
For each child of node:
v = max(v, minimax(child, depth - 1, alpha, beta, False))
alpha = max(alpha, v)
If beta <= alpha, break (pruning).
If maximizingPlayer is false:
Initialize v to positive infinity.
For each child of node:
v = min(v, minimax(child, depth - 1, alpha, beta, True))
beta = min(beta, v)
If beta <= alpha, break (pruning).
Return v.
PROGRAM:
def evaluate(board):
# Check rows, columns, and diagonals for a win
for row in board:
if all(cell == 'X' for cell in row):
return 1 # Player X wins
elif all(cell == 'O' for cell in row):
return -1 # Player O wins
21

for col in range(3):
if all(board[row][col] == 'X' for row in range(3)):
return 1 # Player X wins
elif all(board[row][col] == 'O' for row in range(3)):
return -1 # Player O wins
if all(board[i][i] == 'X' for i in range(3)) or all(board[i][2 - i] == 'X' for i in range(3)):
return 1 # Player X wins
if all(board[i][i] == 'O' for i in range(3)) or all(board[i][2 - i] == 'O' for i in range(3)):
return -1 # Player O wins
# Check for a draw
if all(cell != ' ' for row in board for cell in row):
return 0 # Draw
# Game still ongoing
return None
def is_terminal(board):
return evaluate(board) is not None
def minimax(board, depth, maximizingPlayer):
if depth == 0 or is_terminal(board):
return evaluate(board)
if maximizingPlayer:
maxEval = float('-inf')
for i in range(3):
for j in range(3):
if board[i][j] == ' ':
board[i][j] = 'X'
eval = minimax(board, depth - 1, False)
board[i][j] = ' ' # Undo the move
maxEval = max(maxEval, eval)
return maxEval
else:
minEval = float('inf')
for i in range(3):
for j in range(3):
if board[i][j] == ' ':
board[i][j] = 'O'
eval = minimax(board, depth - 1, True)
board[i][j] = ' ' # Undo the move
minEval = min(minEval, eval)
return minEval
def best_move(board):
bestVal = float('-inf')
bestMove = None
for i in range(3):
22

for j in range(3):
if board[i][j] == ' ':
board[i][j] = 'X'
moveVal = minimax(board, 9, False) # Depth is set to 9 for Tic-Tac-Toe
board[i][j] = ' ' # Undo the move
if moveVal > bestVal:
bestMove = (i, j)
bestVal = moveVal
return bestMove
def print_board(board):
for row in board:
print(" ".join(row))
if __name__ == "__main__":
# Example usage for Tic-Tac-Toe
initial_board = [[' ', ' ', ' '], [' ', ' ', ' '], [' ', ' ', ' ']]
while not is_terminal(initial_board):
print_board(initial_board)
player_move = tuple(map(int, input("Enter your move (row and column): ").split()))
initial_board[player_move[0]][player_move[1]] = 'O'
if is_terminal(initial_board):
break
print_board(initial_board)
ai_move = best_move(initial_board)
print(f"AI's move: {ai_move}")
initial_board[ai_move[0]][ai_move[1]] = 'X'
result = evaluate(initial_board)
print_board(initial_board)
if result == 1:
print("Player X wins!")
elif result == -1:
print("Player O wins!")
else:
print("It's a draw!")
OUTPUT:
Enter your move (row and column): 1
RESULT:
Thus the above program was implemented and executed successfully.
23

EX Solve constraint satisfaction problems
NO:4
Aim:
To Solve constraint satisfaction problems.
Procedure:
CONSTRAINT
In this example, we have three variables (A, B, and C) that need to be assigned
values from the set [1, 2, ..., 9]. The goal is to find assignments that satisfy a
specific constraint, in this case, the sum of A, B, and C should be equal to 15, and
the values of A, B, and C should be distinct.
PROGRAM:
from itertools import product
def is_valid_assignment(assignment):
# Check constraints for the assignment
a, b, c = assignment
return a + b + c == 15 and len(set(assignment)) == 3
def print_solution(assignments):
# Print valid assignments
for assignment in assignments:
print(f"A: {assignment[0]}, B: {assignment[1]}, C: {assignment[2]}")
print()
def solve_csp():
variables = [1, 2, 3, 4, 5, 6, 7, 8, 9]
domains = [variables, variables, variables]
# Generate all possible combinations of assignments
all_assignments = list(product(*domains))
24

# Filter valid assignments based on constraints
valid_assignments = [assignment for assignment in all_assignments if
is_valid_assignment(assignment)]
# Print the solutions
print_solution(valid_assignments)
if __name__ == "__main__":
solve_csp()
OUTPUT:
A: 1, B: 5, C: 9
A: 1, B: 6, C: 8
A: 1, B: 8, C: 6
A: 1, B: 9, C: 5
A: 2, B: 4, C: 9
A: 2, B: 5, C: 8
A: 2, B: 6, C: 7
A: 2, B: 7, C: 6
A: 2, B: 8, C: 5
A: 2, B: 9, C: 4
A: 3, B: 4, C: 8
A: 3, B: 5, C: 7
A: 3, B: 7, C: 5
A: 3, B: 8, C: 4
A: 4, B: 2, C: 9
A: 4, B: 3, C: 8
A: 4, B: 5, C: 6
A: 4, B: 6, C: 5
A: 4, B: 8, C: 3
A: 4, B: 9, C: 2
A: 5, B: 1, C: 9
A: 5, B: 2, C: 8
25

A: 5, B: 3, C: 7
A: 5, B: 4, C: 6
A: 5, B: 6, C: 4
A: 5, B: 7, C: 3
A: 5, B: 8, C: 2
A: 5, B: 9, C: 1
A: 6, B: 1, C: 8
A: 6, B: 2, C: 7
A: 6, B: 4, C: 5
A: 6, B: 5, C: 4
A: 6, B: 7, C: 2
A: 6, B: 8, C: 1
A: 7, B: 2, C: 6
A: 7, B: 3, C: 5
A: 7, B: 5, C: 3
A: 7, B: 6, C: 2
A: 8, B: 1, C: 6
A: 8, B: 2, C: 5
A: 8, B: 3, C: 4
A: 8, B: 4, C: 3
A: 8, B: 5, C: 2
A: 8, B: 6, C: 1
A: 9, B: 1, C: 5
A: 9, B: 2, C: 4
A: 9, B: 4, C: 2
A: 9, B: 5, C: 1
RESULT:
Thus the above program was implemented and executed successfully.
26

EX Implement propositional model checking algorithms
NO:5
Aim:
To Implement propositional model checking algorithms .
ALGORITHM:
Algorithm: Simple Propositional Model Checking
Input:
formula: Propositional formula to be checked.
model: Dictionary representing the variable assignments in the model.
Procedure:
If formula is a variable, return the value assigned to that variable in the model.
If formula is a negation, recursively evaluate the negated formula and return the negation of
the result.
If formula is a conjunction, recursively evaluate both sub-formulas and
return the conjunction of the results.
If formula is a disjunction, recursively evaluate both sub-formulas and
return the disjunction of the results.
If formula is an implication, recursively evaluate both sub-formulas and
return the implication result. Otherwise, raise an error for an invalid formula.
Output:
Return the truth value of the formula in the given model.
PROGRAM:
def evaluate_propositional_formula(formula, model):
if formula[0] == 'Var':
# Variable: Check if the variable is True in the model
return model.get(formula[1], False)
elif formula[0] == 'Not':
# Negation: Recursively evaluate the negated formula
27

return not evaluate_propositional_formula(formula[1], model)
elif formula[0] == 'And':
# Conjunction: Recursively evaluate both subformulas
return evaluate_propositional_formula(formula[1], model) and
evaluate_propositional_formula(formula[2], model)
elif formula[0] == 'Or':
# Disjunction: Recursively evaluate both subformulas
return evaluate_propositional_formula(formula[1], model) or
evaluate_propositional_formula(formula[2], model)
elif formula[0] == 'Implies':
# Implication: Recursively evaluate both subformulas
return not evaluate_propositional_formula(formula[1], model) or
evaluate_propositional_formula(formula[2], model)
else:
raise ValueError("Invalid formula")
if __name__ == "__main__":
# Example usage
# Formula: (A and B) or (not C)
propositional_formula = ('Or', ('And', ('Var', 'A'), ('Var', 'B')), ('Not', ('Var', 'C')))
# Model: {'A': True, 'B': False, 'C': True}
model = {'A': True, 'B': False, 'C': True}
result = evaluate_propositional_formula(propositional_formula, model)
print(f"Does the formula hold in the model? {'Yes' if result else 'No'}")
OUTPUT:
Does the formula hold in the model? No
RESULT:
Thus the above program was implemented and executed successfully.
28

EX . Implement forward chaining, backward chaining, and resolution strategies
NO:6
Aim:
To Implement forward chaining, backward chaining, and resolution strategies.
Forward Chaining Algorithm:
Input:
knowledge_base: Rules and facts.
goal: The goal to be achieved.
Procedure:
Initialize an agenda with known facts.
Repeat until the agenda is empty:
Pop a fact from the agenda.
If the fact is the goal, return success.
If the fact is not already inferred:
Add the fact to the inferred set.
Add all conclusions of rules with the fact in their premises to the agenda.
Output:
Return success if the goal is achieved, otherwise return failure.
Backward Chaining Algorithm:
Input:
knowledge_base: Rules and facts.
goal: The goal to be achieved.
explored: Set of explored goals.
Procedure:
If the goal is a known fact, return success.
For each rule in the knowledge base:
If the goal is the conclusion of the rule:
29

Recursively attempt to satisfy each premise of the rule.
If all premises are satisfied, return success.
Return failure.
Output:
Return success if the goal is achieved, otherwise return failure.
Resolution Algorithm:
Input:
knowledge_base: Clauses representing rules and facts.
query: The query to be proven.
Procedure:
Initialize clauses with the knowledge base and the negation of the query.
Repeat until no new clauses can be added:
For each pair of clauses (Ci, Cj):
If there is a resolvent, add it to the set of clauses.
If an empty clause is generated, return success.
If no new clauses are added, return failure.
Output:
Return success if the query is proven, otherwise return failure.
PROGRAM:
def forward_chaining(knowledge_base, goal):
agenda = list(knowledge_base['facts'])
inferred = set()
while agenda:
current_fact = agenda.pop(0)
if current_fact == goal:
return True # Goal achieved
if current_fact not in inferred:
inferred.add(current_fact)
30

agenda.extend(rule['conclusion'] for rule in knowledge_base['rules'] if current_fact in
rule['premises'])
return False # Goal not achieved
def backward_chaining(knowledge_base, goal, explored=None):
if explored is None:
explored = set()
if goal in knowledge_base['facts']:
return True # Goal achieved
for rule in knowledge_base['rules']:
if goal == rule['conclusion'] and goal not in explored:
explored.add(goal)
premises_satisfied = all(backward_chaining(knowledge_base, premise,
explored) for premise in rule['premises'])
if premises_satisfied:
return True
return False # Goal not achieved
def resolution(knowledge_base, query):
clauses = knowledge_base['clauses'] + [frozenset([query])]
new = set()
while True:
for ci in clauses:
for cj in clauses:
if ci != cj:
resolvents = resolve(ci, cj)
if not resolvents:
return True # Goal achieved
new.update(resolvents)
if new.issubset(clauses):
return False # No new information
31

clauses.update(new)
def resolve(ci, cj):
resolvents = set()
for literal in ci:
if frozenset([-literal]) in cj:
resolvent = (ci - {literal}).union(cj - {-literal})
if not resolvent:
return None # Empty clause, contradiction
resolvents.add(frozenset(resolvent))
return resolvents
if __name__ == "__main__":
knowledge_base_forward = {
'facts': {'A', 'B'},
'rules': [
{'premises': {'A'}, 'conclusion': 'C'},
{'premises': {'B', 'C'}, 'conclusion': 'D'},
]
}
goal_forward = 'D'
result_forward = forward_chaining(knowledge_base_forward, goal_forward)
print(f"Forward Chaining: Can we derive {goal_forward}? {'Yes' if result_forward else
'No'}")
knowledge_base_backward = {
'facts': {'D'},
'rules': [
32

{'premises': {'A'}, 'conclusion': 'C'},
{'premises': {'B', 'C'}, 'conclusion': 'D'},
]
}
goal_backward = 'A'
result_backward = backward_chaining(knowledge_base_backward, goal_backward)
print(f"Backward Chaining: Can we derive {goal_backward}? {'Yes' if
result_backward else 'No'}")
knowledge_base_resolution = {
'clauses': [frozenset({-1, 2}), frozenset({-2, 3}), frozenset({-3})],
}
query_resolution = -1
result_resolution = resolution(knowledge_base_resolution, query_resolution)
print(f"Resolution: Can we derive {query_resolution}? {'Yes' if
result_resolution else No'}")
OUTPUT:
Forward Chaining: Can we derive D? Yes
Backward Chaining: Can we derive A? No
Resolution: Can we derive -1? Yes
RESULT:
Thus the above program was implemented and executed successfully.
33

EX Build naïve Bayes models
NO:7
Aim:
To Build naïve Bayes models.
Naive Bayes Algorithm:
Training:
Input:
Training dataset with labeled examples.
Procedure:
Calculate the prior probabilities for each class.
For each feature in the dataset:
Calculate the likelihood probabilities for each class given the feature.
Smooth probabilities if needed (e.g., using Laplace smoothing).
Store the prior and likelihood probabilities.
Prediction:
Input:
Test example.
Procedure:
For each class:
Calculate the product of prior probability and likelihood probabilities for each feature.
Assign the class with the highest probability to the test example.
PROGRAM:
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, classification_report
# Example data
corpus = [
34

{'text': 'this is a positive example', 'label': 'positive'},
{'text': 'negative sentiment here', 'label': 'negative'},
{'text': 'a positive message', 'label': 'positive'},
{'text': 'I dislike this', 'label': 'negative'},
# Add more examples as needed
]
# Extract features and labels
texts = [example['text'] for example in corpus]
labels = [example['label'] for example in corpus]
# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(texts, labels,
test_size=0.2, random_state=42) # Vectorize the text data using bag-of-
words representation
vectorizer = CountVectorizer()
X_train_vectorized = vectorizer.fit_transform(X_train)
X_test_vectorized = vectorizer.transform(X_test)
# Train a Multinomial Naive Bayes classifier
naive_bayes_classifier = MultinomialNB()
naive_bayes_classifier.fit(X_train_vectorized, y_train)
# Make predictions on the test set
predictions = naive_bayes_classifier.predict(X_test_vectorized)
# Evaluate the classifier
accuracy = accuracy_score(y_test, predictions)
print(f"Accuracy: {accuracy:.2f}")
# Display classification report
print("Classification Report:")
print(classification_report(y_test, predictions))
35

# Display predictions for the test set
print("\nPredictions for the test set:")
for text, true_label, predicted_label in zip(X_test, y_test, predictions):
print(f"Text: {text}, True Label: {true_label}, Predicted Label: {predicted_label}")
OUTPUT:
Accuracy: 0.00
Classification Report:
precision recall f1-score support
negative 0.00 0.00 0.00 1.0
positive 0.00 0.00 0.00 0.0
accuracy 0.00 1.0
macro avg 0.00 0.00 0.00 1.0
weighted avg 0.00 0.00 0.00 1.0
Predictions for the test set:
Text: negative sentiment here, True Label: negative, Predicted Label: positive
RESULT:
Thus the above program was implemented and executed successfully.
36

EX Implement Bayesian networks and perform inferences
NO:8
Aim:
To Implement Bayesian networks and perform inferences
ALGORITHM:
Define the Bayesian Network structure: Specify the nodes and edges in the network.
Estimate Conditional Probability Distributions (CPDs): Use the
ParameterEstimator to estimate CPDs based on your data.
Assign CPDs to the model: Add the estimated CPDs to the Bayesian network.
Check model structure and CPDs: Print the structure and CPDs to verify correctness.
Perform inference using VariableElimination: Use the
VariableElimination method for inference. Display the inference result:
Print the result of the inference.
PROGRAM:
from pgmpy.models import BayesianModel
from pgmpy.estimators import ParameterEstimator
from pgmpy.inference import VariableElimination
# Create a Bayesian network model
model = BayesianModel([('A', 'C'), ('B', 'C')])
# Define conditional probability distributions (CPDs)
cpd_a = ParameterEstimator(model).estimate_cpd('A')
cpd_b = ParameterEstimator(model).estimate_cpd('B')
# Assign CPDs to the model
model.add_cpds(cpd_a, cpd_b)
# Check model structure and CPDs
print("Model Structure:")
print(model.edges())
print("\nCPD for A:")
37

print(model.get_cpds('A'))
print("\nCPD for B:")
print(model.get_cpds('B'))
# Perform inference using VariableElimination
inference = VariableElimination(model)
query = inference.query(variables=['C'], evidence={'A': 1, 'B': 0})
print("\nInference Result:")
print(query)
OUTPUT:
Collecting pgmpy
Downloading pgmpy-0.1.24-py3-none-any.whl (2.0 MB)
Requirement already satisfied: scipy in c:\users\a\anaconda3\lib\site-packages
(from pgmpy) (1.7.3) Requirement already satisfied: numpy in
c:\users\a\anaconda3\lib\site-packages (from pgmpy) (1.21.5) Requirement
already satisfied: pandas in c:\users\a\anaconda3\lib\site-packages (from
pgmpy) (1.4.2) Requirement already satisfied: statsmodels in
c:\users\a\anaconda3\lib\site-packages (from pgmpy) (0.13.2) Requirement
already satisfied: joblib in c:\users\a\anaconda3\lib\site-packages (from
pgmpy) (1.1.0) Requirement already satisfied: pyparsing in
c:\users\a\anaconda3\lib\site-packages (from pgmpy) (3.0.4) Requirement
already satisfied: tqdm in c:\users\a\anaconda3\lib\site-packages (from pgmpy)
(4.64.0) Downloading pgmpy-0.1.23-py3-none-any.whl (1.9 MB)
Downloading pgmpy-0.1.22-py3-none-any.whl (1.9 MB)
Downloading pgmpy-0.1.21-py3-none-any.whl (1.9 MB)
Downloading pgmpy-0.1.20-py3-none-any.whl (1.9 MB)
Downloading pgmpy-0.1.19-py3-none-any.whl (1.9 MB)
Downloading pgmpy-0.1.18-py3-none-any.whl (1.9 MB)
Downloading pgmpy-0.1.17-py3-none-any.whl (1.9 MB)
Downloading pgmpy-0.1.16-py3-none-any.whl (1.9 MB)
Downloading pgmpy-0.1.15-py3-none-any.whl (1.9 MB)
Downloading pgmpy-0.1.14-py3-none-any.whl (331 kB)
Downloading pgmpy-0.1.13-py3-none-any.whl (324 kB)
Downloading pgmpy-0.1.12-py3-none-any.whl (322 kB)
Downloading pgmpy-0.1.11-py3-none-any.whl (314 kB)
Downloading pgmpy-0.1.10-py3-none-any.whl (339 kB)
Downloading pgmpy-0.1.9-py3-none-any.whl (331 kB)
Installing collected packages: pgmpy
Successfully installed pgmpy-0.1.9
RESULT:
Thus, the program to implement Bayesian Networks and perform inferences is
implemented and executed successfully.
38