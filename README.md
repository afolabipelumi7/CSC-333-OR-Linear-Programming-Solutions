# CSC-333-OR-Linear-Programming-Solutions
 COMPUTATION AND NUMERICAL ANALYSIS :A detailed README file describing the steps, methodology, and any  instructions on running the Python code.


LAB PRACTICAL 1
ASSIGNMENT ON LINEAR PROGRAMMING MODEL -COMPUTATIONAL AND NUMERICAL ANALYSIS.



Run the following command to install the required packages:
```bash
- pip install jupyter
- pip install pandas
- pip install numpy
- pip install matplotlib



example of parameters in the graphical solution-jupyter notebook through out questions from 1-10  
y1 = (12 - 2 * x) / 3 -represents the inequality 

# REPRESENT Constraint 2: x + 2y <= 8
y2 = (8 - x) / 2 represents the inequality 

# Non-negativity constraints
y1 = np.maximum(0, y1)
y2 = np.maximum(0, y2)
This line ensures that the value of y1 is not negative. If y1 is less than 0, it is set to 0 to satisfy the condition that y1 >= 0 (the non-negativity constraint).


plot-Plotting Data Points: It can be used to plot a set of data points. For example, given arrays or lists of x and y values, the plot function connects these points with a line (by default), creating a graph.
# Plot the constraints
plt.plot(x, y1, label=r'$2x + 3y \leq 12$')
plt.plot(x, y2, label=r'$x + 2y \leq 8$')
# Shade the feasible region
plt.fill_between(x, np.minimum(y1, y2), where=(x >= 0), color='grey', alpha=0.5)




The line of code:
x = np.linspace(0, 20, 400) is used to create an array of evenly spaced values for the variable x within a specified range. Here's a detailed explanation:

Function Used: np.linspace(start, stop, num)
np.linspace is a function from the NumPy library that generates a sequence of evenly spaced numbers within a given range.
Arguments:
start: The beginning of the interval (here,0).
stop: The end of the interval (here,20).
num: The number of points to generate (here, 400).
Purpose in the Code:

The array x represents thex-axis values used for plotting constraints and objective functions in the graphical method. It acts as the independent variable in constraints, which are functions of both and y.
This method is commonly used in numerical computing and data visualization to handle continuous variables for analysis and plotting.

Explanation of Code Line 2
The line of code:
np.clip

python
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

EXPLANATION OF THIS PART-#very important
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

plt.xlabel(r'$x$'): This sets the label for the x-axis of the plot. The r before the string indicates it's a raw string, and the '$x$' uses LaTeX formatting to display the label as "x" in a mathematical style.

plt.ylabel(r'$y$'): This sets the label for the y-axis of the plot. Similar to the x-axis label, the r and '$y$' format the label using LaTeX as a mathematical symbol.

plt.axhline(0, color='black',linewidth=0.5): This adds a horizontal line (x-axis) at y=0. The color='black' specifies the line color, and linewidth=0.5 sets the thickness of the line.

plt.axvline(0, color='black',linewidth=0.5): This adds a vertical line (y-axis) at x=0. Again, color='black' and linewidth=0.5 control the appearance of the line.

plt.grid(color='gray', linestyle='--', linewidth=0.5): This enables a grid on the plot, with the grid lines colored gray, dashed ('--'), and with a line width of 0.5.

plt.legend(): This shows the legend on the plot. The legend displays labels for the plotted data if any labels are provided in the plot (typically used with plot commands that have a label parameter).

plt.title('Feasible Region and Optimal Solution'): This sets the title of the plot, which will be displayed at the top of the plot. The title here is 'Feasible Region and Optimal Solution'.

plt.show(): This displays the plot. It must be called to visualize the plot if you're running the code in a script or a non-interactive environment.


The constraints are valid only for non-negative values of both 
x and 𝑦 (i.e.,x≥0,y≥0).
Clipping ensures that any calculated y values that fall below zero (due to the constraints) are disregarded, ensuring that the graph remains consistent with the problem's domain.

Explanation of Code Line 3
The line of code: python plt.fill_between(x, np.minimum(np.minimum(y1, y2), y3), 0, color='gray', alpha=0.3, label='Feasible Region')
This line uses the plt.fill_between() function from Matplotlib to shade the feasible region defined by the constraints. Here's a breakdown:

Arguments:
x: The array of x-coordinates for the shaded region.
np.minimum(np.minimum(y1, y2), y3): The y-coordinates for shading, which are calculated as the minimum of y1, y2, and y3 at each x-coordinate.
0: The lower boundary for the shading, set to 0 in order to fill the area below the constraints.
color='gray': The color of the shaded region (gray).
alpha=0.3: The transparency level of the shaded region (30% opacity).
label='Feasible Region': The label for the shaded area.

Solving Using the linprog Function from SciPy
The linprog function from the SciPy library is used to solve linear programming problems. Here's a brief overview of how it works:
The linprog function minimizes a linear objective function subject to linear equality and inequality constraints.




