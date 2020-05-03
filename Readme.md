# Programming Paradigms

### Time measurement of iterative and recursive procedures

**Computational complexity** is a field from computer science which analyzes algorithms based on the amount resources required for running it. The amount of resources required depends on the input size (say $n$). When analyzing an algorithm we can consider the time complexity and space complexity. 

The **space complexity** is the amount of memory space required to solve a problem in relation to the input size.

The **time complexity** is the computational complexity that describes the amount of time it takes to run an algorithm.There are three cases When analyzing the time complexity: best-case, average-case and worst-case. 

- **Best case** is the function which performs the minimum number of steps on input data of $n$ elements. 
- **Worst case** is the function which performs the maximum number of steps on input data of size $n$. 
- **Average case** is the function which performs an average number of steps on input data of $n$ elements.

A **recursive function** is a function that calls itself in specific conditions. e.g.  Fibonacci number sequence, factorial function, quick sort etc. 

An **Iterative function** is loop based imperative repetitions of a process.

![](IR.png)

### Examples of Iteration and Recursion
- Traversal of trees: Recursive
- Dynamic Programming: Both recursive and Iterative
- Traversal of linear Data Structure: Iterative
- Depth-First Search: Recursive
- Breadth-First Search: Iterative
- Backtracking Algorithms: Recursive
- Divide-and-Conquer problems: Recursive in nature.
- Hash Table: Iterative
- Greedy: Both recursive and Iterative
- BST: Both Iterative and Recursive

## Big-O Notation
Big-O notation(asymptotic notation) is a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity.

## Factorial 
The factorial of a positive integer $n$, denoted by $n!$, is the product of all positive integers less than or equal to $n$. The value of 0! and 1! is 1. Mathematically,
$n!=n(n-1)(n-2)...3.2.1$

```python
#factorial Recursive Python Code
 def factorial_recursion(n):  
    	if n < 0:
        	print("No factorial for the number you selected")
    	elif n== 0:  
       		return 1
   		elif n== 1:  
       		return 1
    	else:  
       		return n*factorial_recursion(n-1)
```
The complexity factor of recursive time is $O(n)$.


## Fibonacci Sequence
The Fibonacci Sequence is the series of numbers:
$$0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ... $$
The next number is found by adding up the two numbers before it.

```python
def fibonacci_recursive(n):
    if n < 0: #Factorial doesn't exist for negative integers
        print("n must be positive")
    elif n== 0:  
       return n
    elif n== 1:   #initial stage
       return n
    # Recursive case
    else:
        return fibonacci_recursive(n-1) + fibonacci_recursive(n-2)
```

#### Run-time Analysis
We know that the recursive equation for Fibonacci is $T(n)=T(n-1)+T(n-2)+O(1)$. You can check [here](https://www.geeksforgeeks.org/time-complexity-recursive-fibonacci-program/) for the detailed solution to the recursive equation. The running time is exponential given by $O(1.6180)^n$.
- Time complexity of recursive code is $O(1.6180)^n$.
- Time Complexity of iterative code is $O(n)$.



## Binary search
 Binary search is a search algorithm that finds the position of a target value within a sorted array.  It works by repeatedly dividing in half the portion of the list that could contain the item, until you've narrowed down the possible locations to just one. 

 ```python
#binary search function 
def binary_search(arraylist, find): 
    while len(arraylist) > 0: 
        middle = (len(arraylist))//2 #divide and conquer
        if arraylist[middle] == find: 
            return True
        elif arraylist[middle] < find: 
            arraylist = arraylist[:middle] 
        else: 
            arraylist = arraylist[middle + 1:] 
    return False
 ```

Steps of the binary search:
- Starting from the middle of the list.
- If the searched value is lower than the value in the middle of the list, set a new right bounder.
- If the searched value is higher than the value in the middle of the list, set a new left bounder.
- If the search value is equal to the value in the middle of the list, return the middle (the index).
- Repeat the steps above until the value is found or the left bounder is equal or higher the right bounder.

#### Run-time Analysis
Binary search is a fast search algorithm with run-time complexity of $O(log_2n)$, where $n$ is total number of elements in the list. This search algorithm works on the principle of divide and conquer.

## Linear Search
A linear search or sequential search is a method for finding an element within a list, the list not neccesarily need to be sorted. It sequentially checks each element of the list until a match is found or the whole list has been searched.
```python
# linear search function 
def linear_search(mylist, value): 
    for x in mylist: 
        if x == value: 
            return True # if the value is in the list
    return False #if the value is not in the list 
```
```python
#Test the code with this list 
linear_search([1,3,6,5,15,9,11], 15)
```
The python code will return **True**, since 15 is part of the list.  A linear search scans one item at a time, without jumping to any item .

- Worst complexity: $O(n)$
- Average complexity: $O(n)$


  
## Insertion Sort
Insertion sort is a simple sorting algorithm that builds the final sorted array (or list) one item at a time. It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort.

```python

#Function to do insertion sort 
def insertionSort(array): 
    # Traverse through 1 to the length of the array 
    for i in range(1, len(array)): 
  
        key = array[i] 
  
        # Move elements of arr[0..i-1], that are 
        # greater than key, to one position ahead 
        # of their current position 
        j = i-1
        while j >= 0 and key < array[j] : 
                array[j + 1] = array[j] 
                j -= 1
        array[j + 1] = key 
    return array
```
```python
array = [12, 11, 13, 5, 6] 
insertionSort(array)
```
`Output:  [5, 6, 11, 12, 13]`

#### Run-time Analysis
 In this sorting, during ith iteration, the ﬁrst $(i-1)$ elements are sorted and ith card is inserted to the correct
place by performing linear search on the ﬁrst $(i-1)$ elements. This algorithm performs well on smaller
inputs and on inputs that are already sorted.

We shall analyze the run time of insertion sort by considering its worst case and best case behavior. From the code, the cost (the number of times the line is executed) incurred
in best and worst case inputs is given. 
Alternatively, the cost can also be obtained using recurrence relation. Recurrence relation in worst case: $T(n)=T(n-1)+n-1, T(2) = 1$, solving this using substitution
method or recurrence tree method yields $T(n) = O(n^2)$. 

Recurrence relation in best case: $T(n)=T(n-1)+1,T(2)=1$, and the solution is $T(n) = O(n).$

Insertion sort takes maximum time to sort if elements are sorted in reverse order. And it takes minimum time (order of $n$) when elements are already sorted.




## Heap Permutation
Heap's algorithm generates all possible permutations of n objects. The algorithm is going to swap elements based on the iteration k we are in for the current size n. If this iteration k is even then we will swap the kth element with the last element, and else we will swap the last element with the first element.

```python
def heap_permutation(data, n):
    if n == 1:
        print(data)
        return
    
    for i in range(n):
        heap_permutation(data, n - 1)
        if n % 2 == 0:
            data[i], data[n-1] = data[n-1], data[i]
        else:
            data[0], data[n-1] = data[n-1], data[0]
    
if __name__ == '__main__':
    data = [3,6,7]
    heap_permutation(data, len(data))
```

```
#Output
[3, 6, 7]
[6, 3, 7]
[7, 3, 6]
[3, 7, 6]
[6, 7, 3]
[7, 6, 3]
```
#### Run-time Analysis
The ruuning time of Heap's permutation will grow in a factorial way, based on the size of the input data. If the input is of size $n$, algorithm has factorial time complexity $O(n!)$.



## QuickSort
Quick sort is another sorting algorithm that follows divide and conquer strategy. In this sorting, we pick a
special element (pivot element) and the given array is partitioned with respect to the pivot element. Elements
that are smaller than the pivot element will be in one partition and the elements that are greater than the pivot element will be in another
partition. This process is done recursively till sub problem size becomes one.

Different ways of picking the pivot: 
- Always pick first element as pivot.
- Always pick last element as pivot (implemented below)
- Pick a random element as pivot.
- Pick median as pivot.

```python
# This function takes last element as pivot, places 
# the pivot element at its correct position in sorted 
# array, and places all smaller (smaller than pivot) 
# to left of pivot and all greater elements to right 
# of pivot 
def partition(arr,low,high): 
    i = ( low-1 )         # index of smaller element 
    pivot = arr[high]     # pivot 
  
    for j in range(low , high): 
  
        # If current element is smaller than the pivot 
        if   arr[j] < pivot: 
          
            # increment index of smaller element 
            i = i+1 
            arr[i],arr[j] = arr[j],arr[i] 
  
    arr[i+1],arr[high] = arr[high],arr[i+1] 
    return ( i+1 ) 
  
# The main function that implements QuickSort 
# arr[] --> Array to be sorted, 
# low  --> Starting index, 
# high  --> Ending index 
  
# Function to do Quick sort 
def quickSort(arr,low,high): 
    if low < high: 
  
        # pi is partitioning index, arr[p] is now 
        # at right place 
        pi = partition(arr,low,high) 
  
        # Separately sort elements before 
        # partition and after partition 
        quickSort(arr, low, pi-1) 
        quickSort(arr, pi+1, high) 
  
# Driver code to test above 
arr = [10, 7, 8, 9, 1, 5] 
n = len(arr) 
quickSort(arr,0,n-1) 
print ("Sorted array is:") 
for i in range(n): 
    print ("%d" %arr[i]) 
```
`Sorted array is:
1
5
7
8
9
10`

#### Run-time Analysis
The recursion for quick sort depends the size of recursive sub problem generated at each stage of the recursion. Since the pivot can take any value, the size of a sub problem can take any value in the range
$[0..n-1]$. 
- Best case: $O(n log_2 n)$
- Worst case: $O(n^2)$

## Tower of Hanoi
Tower of Hanoi is a mathematical puzzle where we have three rods and n disks. The objective of the puzzle is to move the entire stack to another rod, obeying the following simple rules:
1. Only one disk can be moved at a time.
2. Each move consists of taking the upper disk from one of the stacks and placing it on top of another stack i.e. a disk can only be moved if it is the uppermost disk on a stack.
3. No disk may be placed on top of a smaller disk.

```python
# Recursive Python function to solve tower of hanoi
def TowerOfHanoi(n , source, destination, auxilliary): 
    if n==1: 
        print("Move disk 1 from source",source,"to destination",destination) 
        return
    TowerOfHanoi(n-1, source, auxilliary, destination) 
    print("Move disk",n,"from source", source,"to destination",destination) 
    TowerOfHanoi(n-1, auxilliary, destination, source) 
```
```python
n = 4
TowerOfHanoi(n,'P','R','S')
```
```python
#Output
Move disk 1 from source P to destination S
Move disk 2 from source P to destination R
Move disk 1 from source S to destination R
Move disk 3 from source P to destination S
Move disk 1 from source R to destination P
Move disk 2 from source R to destination S
Move disk 1 from source P to destination S
Move disk 4 from source P to destination R
Move disk 1 from source S to destination R
Move disk 2 from source S to destination P
Move disk 1 from source R to destination P
Move disk 3 from source S to destination R
Move disk 1 from source P to destination S
Move disk 2 from source P to destination R
Move disk 1 from source S to destination R
```
#### Run-time Analysis
The time complexity to find order of moves of discs in Tower of Hanoi problem is $O(2^n)$.


## Final Notes
Thank you for reading. Hope you have a better understanding now!
*Compiled by Hezekiah Adewinbi* 

## References

[Heap Permutation](https://towardsdatascience.com/understanding-time-complexity-with-python-examples-2bda6e8158a7)

[QuickSort](https://www.geeksforgeeks.org/quick-sort/)

[Tower of Honoi](https://www.geeksforgeeks.org/python-program-for-tower-of-hanoi/)

[Iteration vs Recursion](https://afteracademy.com/blog/what-is-the-difference-between-iteration-and-recursion)