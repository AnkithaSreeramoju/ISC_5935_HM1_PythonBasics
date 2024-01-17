# Homework Report

## Personal Details
**Name:** Ankitha Sreeramoju
**Date:** 01-17-2024
**Course:** Data Science meets Health Science
**Instructor:** Olmo Zavala-Romero

## Homework Questions and Answers

#### Answer to Question 1
This Python code defines a recursive function named `myrec` that calculates a mathematical expression based on the input parameter `x`. The function follows the following rules:

1. If `x` is equal to 0, the function returns 0.
2. If `x` is less than 0, it raises a ValueError with the message "The value should be greater than 0."
3. For any positive value of `x`, the function calculates the result using a recursive formula: \(2 \times x - \text{myrec}(x - 1)\).

It's important to note that this recursive approach continues until `x` reaches 0, ensuring that the function eventually reaches a base case. The function is designed to handle positive integer values of `x` and raises an exception for non-positive values.

```python
def myrec(x):
    if x == 0:
        return 0
    elif x < 0:
        raise ValueError("The value should be greater than 0")
    else:
        return 2 * x - myrec(x - 1)
```

#### Answer to Question 2
This Python code defines a function called `basic_io` that takes a folder path as input and returns a dictionary containing information about the files and folders within that directory. The returned dictionary includes the following key-value pairs:

- `'number_files'`: Represents the total number of items (files and folders) in the specified directory.
- `'files'`: Contains a list of all items (files and folders) within the directory, sorted in alphabetical order.
- `'file_or_folder'`: Corresponds to a list indicating whether each item in the directory is a file or a folder.

The function first checks whether the specified folder path exists and is indeed a directory. If the folder does not exist or is not a directory, it prints a message and returns an empty dictionary.

Assuming the folder path is valid, the function then proceeds to list the items in the folder, sort them alphabetically, and populate the dictionary accordingly. For each item, it adds the item's name to the `'files'` list and determines whether it is a file or a folder, appending the respective label ('file' or 'folder') to the `'file_or_folder'` list.

Finally, the function sets the `'number_files'` key in the dictionary to the total number of items in the directory and returns the populated dictionary as the output.

Note: There's a small formatting issue in the code with extra spaces before the `return` statement. I've corrected it in this response.

```python
import os

def basic_io(folder_path):
    output = {'number_files': 0, 'files': [], 'file_or_folder': []}

    if not os.path.exists(folder_path) or not os.path.isdir(folder_path):
        print("Folder does not exist.")
        return output

    items = sorted(os.listdir(folder_path))

    for item in items:
        item_path = os.path.join(folder_path, item)
        output['files'].append(item)
        if os.path.isfile(item_path):
            output['file_or_folder'].append('file')
        elif os.path.isdir(item_path):
            output['file_or_folder'].append('folder')

    output['number_files'] = len(items)
    
    return output
```

### Answer to  Question 3
This Python function, named `add2and3`, takes a matrix as input and calculates the sum of the elements in the second row and the third column of the matrix. Here's a breakdown of the code:

- The function first checks if the matrix has at least 2 rows and 3 columns. If not, it prints "Matrix too small" and returns `None`.

- If the matrix is of sufficient size, it proceeds to calculate the sum of elements in the second row (`row_sum`) by using the `sum` function on the second row of the matrix.

- It also calculates the sum of elements in the third column (`col_sum`) by using a generator expression to sum the elements at index 2 for each row in the matrix.

- The final result is the sum of `row_sum` and `col_sum`, representing the sum of elements in the second row and third column of the matrix.

Note: The code assumes that the input matrix is a list of lists, where each inner list represents a row of the matrix. Additionally, the code could be enhanced by including additional checks to ensure that the matrix is rectangular (consistent number of elements in each row) and that the elements are numeric for accurate summation.
```
def add2and3(matrix):
    if len(matrix) < 2 or len(matrix[0]) < 3:
        print("Matrix too small.")
        return None
    row_sum = sum(matrix[1])
    col_sum = sum(matrix[i][2] for i in range(len(matrix)))
    return row_sum + col_sum
```   

#### Answer to Question 4

This Python function, named `squareme`, utilizes the NumPy library to square the elements of a specified row in a matrix. Here's an explanation of the code:

- The function takes two parameters: `matrix`, which is the input matrix, and `row_number`, which is the index of the row to be squared.

- It first checks if the specified `row_number` is within the valid range (greater than or equal to 0 and less than the number of rows in the matrix). If the specified row is out of bounds, it prints "Row not found" and returns `None`.

- If the row number is valid, it uses NumPy's `np.square` function to square each element in the specified row (`matrix[row_number - 1]`). Note that `row_number - 1` is used to convert the human-readable row number (starting from 1) to the zero-based index expected by Python.

- The squared row is then returned as a NumPy array.

A potential improvement to the function could involve checking whether the input matrix is a valid NumPy array and handling non-numeric elements gracefully to avoid potential errors during the squaring operation.

```
import numpy as np
def squareme(matrix, row_number):
    if row_number < 0 or row_number >= len(matrix):
        print("Row not found.")
        return None
    squared_row = np.square(matrix[row_number - 1])
    return squared_row
```
#### Answer to Question 5
Description for Example 1
The provided Python code uses the Matplotlib library to create a simple animated plot. Here's a breakdown of the code:

1. `import matplotlib.pyplot as plt`: Imports the Matplotlib library for plotting.

2. `import matplotlib`: Additional import for Matplotlib.

3. `import matplotlib.animation as animation`: Imports the animation module from Matplotlib.

4. `import numpy as np`: Imports NumPy, a library for numerical operations in Python.

5. `n = 100`: Defines the number of points in the x-axis.

6. `x = np.linspace(0, 2*np.pi, n)`: Creates an array of `n` evenly spaced values between 0 and \(2\pi\), representing the x-axis values.

7. `y = np.sin(x)`: Calculates the sine of each x-axis value, representing the y-axis values.

8. `fig, ax = plt.subplots(1, 1, figsize=(10, 10))`: Creates a figure and a single subplot with a specified size.

9. `ax.set_title('Basic Plot')`: Sets the title of the plot.

10. `ax.plot(x, y, 'r', label='1')`: Plots the sine curve in red ('r') with a label '1'.

11. `ax.plot(x, y + 0.5, 'g--', label='2')`: Plots another curve shifted by 0.5 units in the y-axis and displayed in green with a dashed line ('g--') and labeled '2'.

12. `ax.set_xlabel("Sopas")`: Sets the x-axis label to "Sopas".

13. `ax.set_ylabel("Pericon")`: Sets the y-axis label to "Pericon".

14. `ax.legend()`: Displays a legend based on the labels provided during plotting.

15. `plt.show()`: Displays the plot.

The code generates a basic plot with two curves, a legend, and axis labels. The x-axis represents "Sopas," and the y-axis represents "Pericon." The first curve is the sine function, and the second curve is a shifted version of the sine function. The resulting plot is displayed in a window.

Description for Example 2
The provided Python code uses the Matplotlib library to create a scatter plot with multiple variations. Here's a breakdown of the code:

1. `import matplotlib.pyplot as plt`: Imports the Matplotlib library for plotting.

2. `import matplotlib`: Additional import for Matplotlib.

3. `import matplotlib.animation as animation`: Imports the animation module from Matplotlib.

4. `import numpy as np`: Imports NumPy, a library for numerical operations in Python.

5. `n = 100`: Defines the number of points in the scatter plot.

6. `x = np.linspace(0, 2*np.pi, n)`: Creates an array of `n` evenly spaced values between 0 and \(2\pi\), representing the x-axis values.

7. `y = np.sin(x)`: Calculates the sine of each x-axis value, representing the y-axis values.

8. `fig, ax = plt.subplots(1, 1, figsize=(10, 10))`: Creates a figure and a single subplot with a specified size.

9. `ax.scatter(x, y, label='simplest')`: Plots a scatter plot using the x and y values with a label 'simplest'.

10. `ax.scatter(x, y - 0.3, color='b', alpha=np.linspace(0, 1, len(x)), label='alpha')`: Adds another scatter plot with the same x values but shifted by -0.3 in the y-axis, using blue color ('b'), varying transparency (`alpha`) from 0 to 1, and labeled 'alpha'.

11. `ax.scatter(x, y - 0.5, c=np.linspace(0, 1, len(x)), label='color')`: Adds another scatter plot with the same x values but shifted by -0.5 in the y-axis, using colors that vary based on the linspace values, and labeled 'color'.

12. `ax.scatter(x, y - 0.8, s=np.linspace(0, 100, len(x)), label='size')`: Adds another scatter plot with the same x values but shifted by -0.8 in the y-axis, with varying marker sizes (`s`) from 0 to 100 based on linspace values, and labeled 'size'.

13. `ax.set_title("Scatter")`: Sets the title of the scatter plot.

14. `ax.legend()`: Displays a legend based on the labels provided during plotting.

15. `plt.show()`: Displays the scatter plot.

The code generates a scatter plot with multiple variations, including transparency, color variation, and marker size based on the specified parameters. Each variation is labeled accordingly in the legend.

```ex1
import matplotlib.pyplot as plt
import matplotlib
import matplotlib.animation as animation
import numpy as np

n = 100
x = np.linspace(0,2*np.pi,n)
y = np.sin(x)


fig, ax = plt.subplots(1,1,figsize=(10,10))
ax.set_title('Basic Plot')
ax.plot(x,y, 'r', label='1')
ax.plot(x,y+.5, 'g--', label='2')
ax.set_xlabel("Sopas")
ax.set_ylabel("Pericon")
ax.legend()
plt.show()
```ex2
import matplotlib.pyplot as plt
import matplotlib
import matplotlib.animation as animation
import numpy as np

n = 100
x = np.linspace(0,2*np.pi,n)
y = np.sin(x)


fig, ax = plt.subplots(1,1,figsize=(10,10))
ax.scatter(x,y, label='simplest')
ax.scatter(x,y-.3, color='b', alpha=np.linspace(0,1,len(x)), label='alpha')    # alpha
ax.scatter(x,y-.5, c=np.linspace(0,1,len(x)), label='color')                   # color
ax.scatter(x,y-.8, s=np.linspace(0,100,len(x)), label='size')                 # Size
ax.set_title("Scatter")
ax.legend()
plt.show()


```

## Additional Comments or Notes

![Screenshot (136)](https://github.com/olmozavala/ISC_5935_HM1_PythonBasics/assets/83494220/04ac6d82-8d63-4dd4-8dac-25f30ebc3bdf)
![Screenshot (135)](https://github.com/olmozavala/ISC_5935_HM1_PythonBasics/assets/83494220/0ee7b440-c6ca-48f4-bba6-a40298f74017)

---

## References (if applicable)

- Google colab
- ChatGpt
