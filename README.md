# CSC-333-OR-Linear-Programming-Solutions
 COMPUTATION AND NUMERICAL ANALYSIS :A detailed README file describing the steps, methodology, and any  instructions on running the Python code.
LAB PRACTICAL 1

 Setting Up the Environment
First, make sure you have the necessary Python libraries installed for graphing and mathematical computations. We'll use matplotlib for plotting graphs and numpy for numerical calculations. You can install them using pip if you haven't already:

bash
Copy code
pip install matplotlib numpy
B. Problem Understanding
In optimization problems, you usually want to maximize or minimize a certain function (like profit or cost), subject to certain constraints (such as available resources).

For the purpose of this guide, we'll solve optimization problems where we graphically find the feasible region and the optimal solution.

C. Starting with a Simple Linear Programming Problem
Let's begin with a simple optimization problem:

Objective: Maximize profit 
𝑃
=
5
𝑥
+
3
𝑦
P=5x+3y
Subject to the constraints:
2
𝑥
+
3
𝑦
≤
12
2x+3y≤12
𝑥
+
2
𝑦
≤
8
x+2y≤8
𝑥
≥
0
x≥0
𝑦
≥
0
y≥0
D. Graphing the Constraints
We need to plot the constraints to find the feasible region, which is the area where all constraints are satisfied. The next step is to plot each constraint.

python
Copy code
import matplotlib.pyplot as plt
import numpy as np

# Define the constraints
x = np.linspace(0, 10, 400)

# Constraint 1: 2x + 3y <= 12
y1 = (12 - 2 * x) / 3

# Constraint 2: x + 2y <= 8
y2 = (8 - x) / 2

# Non-negativity constraints (to avoid negative values)
y1 = np.maximum(0, y1)
y2 = np.maximum(0, y2)

# Plot the constraints
plt.plot(x, y1, label=r'$2x + 3y \leq 12$')
plt.plot(x, y2, label=r'$x + 2y \leq 8$')

# Fill the feasible region
plt.fill_between(x, np.minimum(y1, y2), where=(x >= 0), color='grey', alpha=0.5)

# Mark the corner points
corners = np.array([
    [0, 0],
    [6, 0],
    [0, 4],
    [3, 2]
])

plt.scatter(corners[:, 0], corners[:, 1], color='red')

# Annotate the corner points
for i, txt in enumerate(['(0, 0)', '(6, 0)', '(0, 4)', '(3, 2)']):
    plt.annotate(txt, (corners[i, 0], corners[i, 1]), textcoords="offset points", xytext=(0, 10), ha='center')

# Labels and title
plt.xlabel(r'$x$')
plt.ylabel(r'$y$')
plt.axhline(0, color='black',linewidth=0.5)
plt.axvline(0, color='black',linewidth=0.5)
plt.grid(color = 'gray', linestyle = '--', linewidth = 0.5)
plt.legend()
plt.title('Feasible Region and Optimal Solution')

# Show the plot
plt.show()
E. Identifying Corner Points
From the graph, we can identify the corner points of the feasible region. The corner points are the intersections of the constraints, and the optimal solution often occurs at one of these points. In this example:

Corner points are 
(
0
,
0
)
(0,0), 
(
6
,
0
)
(6,0), 
(
0
,
4
)
(0,4), and 
(
3
,
2
)
(3,2).
F. Evaluating the Objective Function
Now that we have the corner points, we can evaluate the objective function 
𝑃
=
5
𝑥
+
3
𝑦
P=5x+3y at each of these points to find the one that maximizes the profit.

python
Copy code
# Objective function: P = 5x + 3y
def objective(x, y):
    return 5 * x + 3 * y

# Evaluate the objective function at each corner point
profits = []
for corner in corners:
    x, y = corner
    profit = objective(x, y)
    profits.append(profit)

# Find the maximum profit and its corresponding corner
max_profit = max(profits)
max_profit_index = profits.index(max_profit)
optimal_point = corners[max_profit_index]

print(f"Optimal solution: Maximum profit is {max_profit} at point {optimal_point}")
G. Solution Interpretation
The output will tell you the optimal solution that maximizes the profit. For example:

arduino
Copy code
Optimal solution: Maximum profit is 30 at point [6, 0]
This means the maximum profit is 30 when 
𝑥
=
6
x=6 and 
𝑦
=
0
y=0.

H. Adding More Complex Constraints
You can extend this process by adding more constraints and variables. For example:

Objective: Minimize cost 
𝐶
=
3
𝑥
+
4
𝑦
C=3x+4y
Subject to:
𝑥
+
2
𝑦
≥
6
x+2y≥6
2
𝑥
+
𝑦
≥
5
2x+y≥5
You would follow the same steps of plotting the constraints, finding the feasible region, and evaluating the objective function at the corner points.

I. Multiple Objectives
If you have more than one objective (e.g., maximizing both profit and production), you might need to solve a multi-objective optimization problem. This typically involves finding the trade-offs between different objectives.

J. Conclusion
Graphical methods provide a clear and visual way to understand optimization problems and solve linear programming problems efficiently. This approach is particularly useful when you have two variables and linear constraints.

You can now apply this technique to other optimization problems involving different objective functions and constraints.

EXPLANATION OF CODE LINE 1

python
Copy code
x = np.linspace(0, 20, 400)
This line generates an array of evenly spaced values for the variable 
𝑥
x within a specified range. Here's a breakdown:

Function Used: np.linspace(start, stop, num)

np.linspace is a function from the NumPy library that creates evenly spaced numbers over a specified interval.
Arguments:
start: The beginning of the interval (here, 
0
0).
stop: The end of the interval (here, 
20
20).
num: The number of points to generate (here, 
400
400).
Purpose in the Code:

The x array holds the 
𝑥
x-axis values for plotting the constraints and objective function in the graphical method.
It serves as the independent variable for the constraints, which are functions of 
𝑥
x and 
𝑦
y.
This method is commonly used in numerical computing and data visualization to handle continuous variables for analysis and plotting.

EXPLANATION OF CODE LINE 2

python
Copy code
np.clip
y1 = np.clip(y1, 0, None)
y2 = np.clip(y2, 0, None)
y3 = np.clip(y3, 0, None)
The np.clip() function is used to restrict the values in arrays y1, y2, and y3 to be greater than or equal to zero. Here's how it works:

python
Copy code
np.clip(array, min, max)
array: The input array whose values are to be clipped.
min: The lower limit. Values below this will be replaced with the min.
max: The upper limit. Values above this will be replaced with the max.
In this context, the clipping ensures that y1, y2, and y3 contain only non-negative values, which is necessary for correctly plotting constraints in linear programming problems. It prevents negative values from affecting the graphical representation of the constraints.

Effect of np.clip(y1, 0, None):

Negative values in y1 are replaced with 0.
Non-negative values (0 or positive) remain unchanged.
Why Use np.clip Here? For linear programming problems, the constraints typically hold for non-negative variables 
𝑥
x and 
𝑦
y (i.e., 
𝑥
≥
0
,
𝑦
≥
0
x≥0,y≥0). By clipping values below zero, we ensure the graph aligns with the domain of the problem.

EXPLANATION OF CODE LINE 3

python
Copy code
# Shade the feasible region
plt.fill_between(x, np.minimum(np.minimum(y1, y2), y3), 0, color='gray', alpha=0.3, label='Feasible Region')
This line uses plt.fill_between() from Matplotlib to shade the feasible region defined by the constraints. Here's a breakdown:

Function: plt.fill_between(x, y, 0, color='gray', alpha=0.3, label='Feasible Region')
x: The x-coordinates for the shaded region, taken from the x array.
y: The y-coordinates for the shaded region, calculated as the minimum of y1, y2, and y3 at each x-value.
0: The lower boundary for shading (0 in this case).
color='gray': The color of the shaded region (gray).
alpha=0.3: The transparency level of the shading (30% transparency).
label='Feasible Region': A label for the shaded region.
SOLVING USING THE LINPROG FUNCTION FROM SCIPY LIBRARY

The linprog function from SciPy is used to solve linear programming problems. It minimizes a linear objective function subject to constraints. Here's an overview:

Arguments of linprog:

c: Coefficients of the linear objective function to be minimized.
A_ub: Coefficients for the inequality constraints (left-hand side).
b_ub: Values for the inequality constraints (right-hand side).
A_eq: Coefficients for equality constraints (left-hand side).
b_eq: Values for equality constraints (right-hand side).
bounds: Bounds for the variables.
method: The optimization method (default is 'simplex').
The function returns an OptimizeResult object, which contains the solution to the problem. This includes the optimal values of the decision variables that minimize the objective function.

