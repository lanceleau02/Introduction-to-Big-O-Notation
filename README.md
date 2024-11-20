# Introduction to Big-O Notation

Welcome in this introduction to Big-O Notation. I decided to write it to better understand this algorithms analysis method, motivated by the desire to prepare myself for Big Tech coding interviews.

## Table of contents

1. [Overview](#overview)
	1. [Definition](#definition)
	2. [Types of measurement](#types-of-measurement)
	2. [General rules](#general-rules)
2. [Complexities](#complexities)
3. [Third Example](#third-example)
4. [Fourth Example](#fourth-examplehttpwwwfourthexamplecom)

## I - Overview

### 1. Definition

**Big-O Notation** is a mathematical way to describe how the runtime (or space requirement) of an algorithm grows as the size of the input increases. It focuses on the worst-case scenario and provides an upper bound on the growth rate.

It measures algorithm's efficiency based on four principles:

1. **Complexity in terms of input size ($n$):** abstract the efficiency of algorithms from the machines they run on.
2. **Machine independent:** don't care about the stats of the machine.
3. **Basic computer steps:** only examine the basic computer steps of the code.
4. **Time and space:** analyze time and space.

### 2. Types of measurement

In asymptotic analysis, there are three different ways to estimate the efficiency of an algorithm:

1. **Worst Case Analysis (Mostly used):**
	- In the worst-case analysis, we calculate the upper bound on the running time of an algorithm. We must know the case that causes a maximum number of operations to be executed.
	- This is the most commonly used analysis of algorithms, most of the time we consider the case that causes maximum operations.
	- The Big-O Notation is based on it.
2. **Best Case Analysis (Very Rarely used):**
	- In the best-case analysis, we calculate the lower bound on the running time of an algorithm. We must know the case that causes a minimum number of operations to be executed.
3. **Average Case Analysis (Rarely used):**
	- In average case analysis, we take all possible inputs and calculate the computing time for all of the inputs. Sum all the calculated values and divide the sum by the total number of inputs.
	- We must know (or predict) the distribution of cases.

### 3. General rules

1. **Ignore constants:** for example, if an algorithm has a real compexity of $5 \times O(n)$ so $5n$, we ignore constants so its Big-O Notation will be $O(n)$. Why? Because as a function's input moves towards the infinity, constants become less and less significant.
2. **Certain terms dominate others:** it is called *"Big-O Growth Rate"* or *"Big-O Growth Hierarchy"*. Big-O Notation ignore low-oder terms so the following rule can be deduced:

$$O(1) < O(log \space n) < O(n) < O(n \space log \space n) < O(n^2) < O(2^n) < O(n!)$$

Here is a graphic representation to better understand this concept:

![](https://miro.medium.com/v2/resize:fit:720/format:webp/0*P5FlnSY6h2Y7hAE5.png)

## II - Complexities

### 1. $O(1)$ - Constant Time

**$O(1)$ complexity** (constant time complexity) describes an algorithm whose execution time or space requirements remain constant regardless of the input size. This means that the algorithm performs the same number of operations, regardless of whether the input size is 1, 100, or 1 million.

<u>**Characteristics:**</u>

- **Independent from input size ($n$):** the number of steps the algorithm takes does not grow with the size of the input.
- **Efficient:** algorithms with $O(1)$ complexity are typically very fast because they perform a fixed number of operations.
- **Examples:**
	- Expressions that never change (e.g., $100 \times 100000$).
	- Accessing an element in an array by its index (e.g., `arr[5]`).
	- Inserting an element into a hash table (on average).
	- Checking the length of a list (if it is pre-computed)

<u>**Example:**</u>

```Python
def oneFunc():
	x = 5 + (15 * 20) # O(1)
	y = 15 - 2 # O(1)
	print(x + y) # O(1)
```

In this example, each line of this code has a complexity of $O(1)$ so the complexity of the code is:

$$O(1) + O(1) + O(1) = O(1)$$

$$OR$$

$$3 \times O(1) = O(1)$$

We categorize a function to $O(1)$ if and only if all the steps have a complexity of $O(1)$.

### 2. $O(log \space n)$ - Logarithmic Time

**$O(log \space n)$ complexity** (logarithmic time complexity) describes an algorithm where the execution time grows logarithmically with the size of the input. This means that as the input size increases, the number of operations grows much more slowly, proportional to the logarithm of the input size.

<u>**Characteristics:**</u>

- **Logarithmic Growth:** for each doubling of the input size, the number of operations increases by a fixed, smaller amount.
- **Efficient for Large Inputs:** algorithms with $O(log \space n)$ complexity are very efficient for processing large inputs because the work grows slowly.
- **Common in Divide-and-Conquer:** algorithms that repeatedly divide the input into smaller parts often have $O(log \space n)$ complexity.
- **Examples:**
	- **Binary Search:** searching for a value in a sorted array by repeatedly halving the search space.
	- **Tree Traversals:** operations on balanced binary search trees (e.g., insert, delete, or search).

<u>**Logarithms:**</u>

Before going further, we need to understand what a logarithm is. Simply, it's the power that a number needs to be raised to get some other number. In computer science, unless specified otherwise, the number that we want to raise to some power is always 2 (binary systems). This is the theory, now let's see that more in details thanks to an example.

Considering this expression: $2^x = 8$, we want to find the number to which we must raise 2 to find 8. This expression is the equivalent to: $x = log_2(8) = 3$ so $2^3 = 8$. Here it is, this is the basics of logarithms. Now, we can see codes examples.

<u>**Example (recursive):**</u>

```Python
def logFunc(n):
	if (n === 0) # O(1)
		return # O(1)
	n = Math.floor(n / 2) # O(1)
	return logFunc(n) # O(log n)
```

This example is a simple recursive function that repeatedly divides the input `n` by 2 (using `Math.floor()` to ensure the result the following rule can be deduced:is an integer) until `n` reaches 0.

Here is a diagram to schematize its operation with `n = 8`:

<div style="text-align: center">

![](./diagrams/recursive_logFunc.svg)
<small>We skip the last recursive call with `n = 0` to make it easier to understand.</small>

</div>

So, in this example where `n` equals to ${\color{green}8}$ we can see that there is ${\color{lightblue}3}$ levels of execution and in each level### 4. $O(n \space log \space n)$ - Linearithmic Time we divide `n` by ${\color{red}2}$, corresponding to $2^{\color{lightblue}3} = {\color{red}2} \times {\color{red}2} \times {\color{red}2} = {\color{green}8}$.

<u>**Example (iterative):**</u>

```Python
def logFunc(n):
	while (n > 1): # O(log n)
		n = Math.floor(n / 2) # O(1)
```

In this iterative example, the `logFunc()` function repeatedly divides `n` by 2 using a while loop until `n` becomes less than or equal to 1.

Here is a breakdown:

```Text
Iteration 1 : n = 8 / 2 = 4
Iteration 2 : n = 4 / 2 = 2
Iteration 3 : n = 2 / 2 = 1
```

So when we pass in a value of `n`, we'll always need to divide this value `n` by $2(log \space n)$ times to get 1 or we need to do $log \space n$ iterations of the loop before we get 1, so:

$$O(log \space 8) \rarr O(log_2 \space 8) \rarr 2^? = 8 \rarr 2^3 = 8$$

### 3. $O(n)$ - Linear Time

**$O(n)$ complexity** (linear time complexity) describes an algorithm where the execution time grows linearly with the size of the input. This means that as the input size doubles, the number of operations also doubles.

<u>**Characteristics:**</u>

- **Proportional Growth:** the time taken or operations performed are directly proportional to the input size.
- **Common in Iterative Processes:** algorithms that process every element in the input once, typically exhibit $O(n)$ complexity.
- **Scales Well with Moderate Input Sizes:** while it may not be as fast as $O(1)$ or $O(log \space n)$, linear time algorithms are efficient for many use cases.
- **Examples:**
	- **Iterating through an Array:** visiting every element in an array to calculate the sum or find a specific value.
	- **Linear Search:** searching for a value in an unsorted array by examining each element.

<u>**Example:**</u>

```Python
def nFunc(n):
	y = 5 + (15 * 20) # O(1)
	for x in range(0, n): # O(n)
		print(x) # O(1)
```

Here is a simple example with 2 statements. The first statement is a calculation which does not depend on any index so its have a $O(1)$ complexity. The second statement is a simple `for()` loop iterates from 0 to `n` and prints the value of `x`, so the complexity of this statement will be:

$$O(n) \times O(1) = O(n)$$

And as we saw earlier, and according to the *"Big-O Notation Growth Rate"*, the statements with a $O(n)$ complexity dominate the statements with a $O(1)$ complexity, so this code has a complexity of $O(n)$.

### 4. $O(n \space log \space n)$ - Linearithmic Time

**$O(n \space log \space n)$ complexity** (linearithmic time complexity) describes an algorithm where the execution time grows proportionally to the input size $n$, multiplied by the logarithm of $n$. This type of complexity often arises in algorithms that combine linear iteration with a divide-and-conquer approach or efficient sorting mechanisms.

<u>**Characteristics:**</u>

- **Combination of Linear and Logarithmic Work:** the $n$ factor comes from processing all elements, and the $log \space n$ factor arises from repeatedly dividing the problem or performing logarithmic work for each element.
- **Efficient for Large Data Sets:** many optimal sorting algorithms, like Merge Sort and Quick Sort, operate with $O(n \space log \space n)$ complexity.
- **Examples:**
	- **Merge Sort:** divides the array into halves ($log \space n$) and merges them back together in linear time ($n$).
	- **Heap Sort:** builds a binary heap ($O(n)$) and performs repeated heap extractions ($O(log \space n)$).

<u>**Example:**</u>

```Python
def nLogNFunc(n):
	y = n # O(1)
	while (n > 1): # O(log n)
		n = Math.floor(n / 2) # O(1)
		for i in range(1, y + 1): # O(n)
			print(i) # O(1)
```

In this example, the `nLogNFunc()` function takes an integer $n$ as input and performs two main operations in a loop. It first initializes a variable $y$ to $n$ and enters a `while()` loop that continues as long as $n$ is greater than 1. In each iteration of the `while()` loop, $n$ is halved (using integer division), and a `for()` loop runs $y$ times (where $y$ is initially equal to $n$), printing the numbers from 1 to $y$. Since $n$ is halved in each iteration of the `while()` loop, the number of iterations of the `while()` loop is approximately $log2(n)$, and the inner `for()` loop runs $n$ times in the first iteration, $n/2$ times in the second, and so on, resulting in a total time complexity of $O(n \space log \space n)$.

Here is a scheme to better understand:

<div style="text-align: center">

![](./diagrams/nLogNFunc.svg)
<small>The brackets that enclose the printing statements designate
the `for()` loop ($O(n)$) and not the `print()` statements ($O(1)$).</small>

</div>

For each iteration in the `while()` loop, we loop to the full size of $y$, which is the original size of $n$, so each of these inner loops has a complexity of $O(n)$, so the processing time increases linearly with the size of $n$.

Example with an input ($n$) of ${\color{lightblue}4}$: $O(log_{\color{red}2} \space {\color{lightblue}4}) = {\color{green}2}$ because ${\color{green}2}^{\color{red}2} = {\color{lightblue}4}$

Time to bring everything together, $O(n \space log \space n)$ means $O(n \times log \space n)$ so if we insert some values we get: 

$$O({\color{lightblue}4} \times {\color{green}2}) \space because \space log_2({\color{lightblue}4}) = {\color{green}2}$$
 
And if you look to the visualization, it makes sense because for each iteration of the `while()` loop, we iterate trough the entirety of $y$, which is the original value of $n$.

### 5. $O(n^2)$ - Quadratic Time

**$O(n^2)$ complexity** (quadratic time complexity) describes an algorithm where the execution time grows proportionally to the square of the input size. This means that as the input size $n$ doubles, the number of operations increases by a factor of $4 \space (2^2)$.

<u>**Characteristics:**</u>

- **Rapid Growth:** the time taken grows quickly as the input size increases, making $O(n^2)$ less efficient for large inputs.
- **Nested Loops:** algorithms with $O(n^2)$ complexity often involve two nested loops, each iterating through the input.
- **Good for Small Data Sets:** while slow for large inputs, $O(n^2)$ can be acceptable for small or moderately sized inputs.
- **Examples:**
	- **Bubble Sort:** compares adjacent elements in a list and swaps them if needed, requiring nested iterations over the input.
	- **Checking All Pairs:** comparing every possible pair of elements in an array or matrix.

<u>**Example:**</u>

```Python
def square(n):
	for i in range(0, n): # O(n)
		for j in range(0, n): # O(n)
			print(i, j) # O(1)
```

In this example, the `square()` function generates and prints all possible pairs of integers $(i,j)$ where both $i$ and $j$ range from $0$ to $n−1$. It uses two nested loops: the outer loop iterates over $i$ from $0$ to $n−1$, and for each value of $i$, the inner loop iterates over $j$ in the same range. This results in $n^2$ outputs, corresponding to all combinations of $i$ and $j$ within the specified range, effectively creating a two-dimensional matrix.

As usual, here is a scheme to better understand:

<div style="text-align: center">

![](./diagrams/square.svg)

</div>

For $n = 4$ we create a matrix with an area of $i \times j = 4 \times 4 = 4^2 = 16$, which will be equal to the number of cells in the matrix and also happends to be the number of times that the code will execute the `print()` statement. So the real complexity of the function is $O(4^2)$ so $O(n^2)$.

We can also deduce this from the fact that there are two nested `for()` loops, each with a complexity of $O(n)$, so $O(n) \times O(n) = O(n^2)$. That's why, tipically, functions with nested `for()` loops have a $O(n^2)$ complexity.

> Note: the principle is the same for $O(n^3)$, except that there is one more dimension in the matrix.

### 5. $O(2^n)$ - Exponential Time








```Python
def fib(n):
	if n == 0:
		return 0
	if n == 1:
		return 1
	return fib(n - 1) + fib(n - 2)
```

In this example, the fib function computes the $n$-th Fibonacci number using a recursive approach. It is based on the definition of the Fibonacci sequence, where $fib(0) = 0$, $fib(1) = 1$, and each subsequent number is the sum of the two preceding ones: $fib(n) = fib(n−1) + fib(n−2)$. The function checks the base cases $n=0$ and $n=1$, returning 0 and 1 respectively. For larger $n$, the function recursively calls itself twice to compute $fib(n−1)$ and $fib(n−2)$, and sums the results.
