# CSC-333-OR-Linear-Programming-Solutions
 COMPUTATION AND NUMERICAL ANALYSIS :A detailed README file describing the steps, methodology, and any  instructions on running the Python code.
LAB PRACTICAL 1

Run the following command to install the required packages:
```bash
- pip install jupyter
- pip install pandas
- pip install numpy
- pip install matplotlib

The line of code:
x = np.linspace(0, 20, 400)

is used to create an array of evenly spaced values for the variable 
𝑥
x within a specified range. Here's a detailed explanation:

Function Used: np.linspace(start, stop, num)

np.linspace is a function from the NumPy library that generates a sequence of evenly spaced numbers within a given range.
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

The array x represents the 
𝑥
x-axis values used for plotting constraints and objective functions in the graphical method.
It acts as the independent variable in constraints, which are functions of both 
𝑥
x and 
𝑦
y.
This method is commonly used in numerical computing and data visualization to handle continuous variables for analysis and plotting.

Explanation of Code Line 2

The line of code:
np.clip

python
Copy code
y1 = np.clip(y1, 0, None)
y2 = np.clip(y2, 0, None)
y3 = np.clip(y3, 0, None)
The np.clip() function is used to restrict the values of the arrays y1, y2, and y3 to be greater than or equal to zero. Here's how it works:

Function Syntax: np.clip(array, min, max)
array: The input array whose values are to be clipped.
min: The lower limit (minimum value). Values below this threshold are replaced with min.
max: The upper limit (maximum value). Values above this threshold are replaced with max.
In this case, the clipping ensures that all values in y1, y2, and y3 are non-negative, which is crucial for plotting constraints in linear programming problems. It prevents negative values from distorting the graphical representation of the constraints.

Effect of np.clip(y1, 0, None):

This modifies the y1 array such that:
All negative values are set to 0.
All non-negative values (0 or positive) remain unchanged.
Why Use np.clip? In the context of solving linear programming (LP) problems graphically:

The constraints are valid only for non-negative values of both 
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
x≥0,y≥0).
Clipping ensures that any calculated y values that fall below zero (due to the constraints) are disregarded, ensuring that the graph remains consistent with the problem's domain.
Explanation of Code Line 3

The line of code:

python
Copy code
plt.fill_between(x, np.minimum(np.minimum(y1, y2), y3), 0, color='gray', alpha=0.3, label='Feasible Region')
This line uses the plt.fill_between() function from Matplotlib to shade the feasible region defined by the constraints. Here's a breakdown:

Arguments:
x: The array of x-coordinates for the shaded region.
np.minimum(np.minimum(y1, y2), y3): The y-coordinates for shading, which are calculated as the minimum of y1, y2, and y3 at each 
𝑥
x-coordinate.
0: The lower boundary for the shading, set to 0 in order to fill the area below the constraints.
color='gray': The color of the shaded region (gray).
alpha=0.3: The transparency level of the shaded region (30% opacity).
label='Feasible Region': The label for the shaded area.
Solving Using the linprog Function from SciPy

The linprog function from the SciPy library is used to solve linear programming problems. Here's a brief overview of how it works:

The linprog function minimizes a linear objective function subject to linear equality and inequality constraints.
Arguments:
c: Coefficients of the linear objective function to minimize.
A_ub: Coefficients for inequality constraints (left-hand side).
b_ub: Values for the inequality constraints (right-hand side).
A_eq: Coefficients for equality constraints (left-hand side).
b_eq: Values for the equality constraints (right-hand side).
bounds: The bounds for the variables.
method: The optimization method used (default is 'simplex').
The linprog function returns an OptimizeResult object that contains the solution to the linear programming problem. This includes the op



