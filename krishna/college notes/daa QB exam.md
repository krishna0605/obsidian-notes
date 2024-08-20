Here are the answers to your questions based on the content from the provided document:

### 1) a) Define and explain the terms “Time complexity” and “Space complexity” of algorithms.

**Time Complexity**: Time complexity refers to the computational time that an algorithm takes to complete as a function of the size of the input data. It is often expressed using Big-O notation, which classifies algorithms according to their worst-case or average-case running time. The time complexity can be categorized into three cases:
- **Best Case**: The minimum time required for the algorithm to complete.
- **Average Case**: The expected time taken for a random input.
- **Worst Case**: The maximum time taken for any input of size n.

**Space Complexity**: Space complexity measures the amount of memory space required by an algorithm as a function of the size of the input data. It includes both the fixed part (independent of input size) and the variable part (dependent on input size). The space requirement can be expressed as:
$ S(P) = c + S_p(\text{Instance characteristics}) $
where $ c $ is a constant representing the fixed part, and $ S_p $ is the space needed based on the input characteristics [T3].

### 1) b) Explain about Amortized Analysis.

**Amortized Analysis**: Amortized analysis is a technique used to analyze the time complexity of an algorithm over a sequence of operations, rather than on a single operation. It provides a more accurate average time per operation when the worst-case time for a single operation is high but occurs infrequently. 

For example, in a dynamic array, when the array is full and a new element is added, the array must be resized, which is a costly operation. However, this resizing does not happen with every insertion. Amortized analysis allows us to average out the cost of resizing over multiple insertions, leading to a more favorable average time complexity for the insert operation [T2].

### 2) Explain in brief about Asymptotic Notations with examples.

**Asymptotic Notations**: Asymptotic notations are mathematical tools used to describe the behavior of functions as the input size grows towards infinity. They help in classifying algorithms based on their performance and efficiency. The most common asymptotic notations are:

- **Big-O Notation (O)**: Represents an upper bound on the time complexity. For example, if an algorithm runs in $ O(n^2) $, it means that the running time grows at most quadratically with the input size.
  
- **Big-Omega Notation (Ω)**: Represents a lower bound on the time complexity. For instance, if $ f(n) = Ω(n) $, it indicates that the algorithm will take at least linear time for large inputs.

- **Big-Theta Notation (Θ)**: Represents a tight bound on the time complexity, meaning the function grows at the same rate both in the upper and lower bounds. For example, $ f(n) = Θ(n \log n) $ indicates that the algorithm's running time grows proportionally to $ n \log n $ [T1].

### 3) Explain about Amortized analysis.

**Amortized Analysis**: As previously mentioned, amortized analysis is a method for analyzing the average time complexity of an algorithm over a sequence of operations. It is particularly useful when certain operations are expensive but infrequent. 

For example, consider a dynamic array that doubles its size when it runs out of space. The cost of resizing is high, but it happens infrequently. By analyzing the total cost of a series of insertions, we can show that the average cost per insertion remains constant, leading to an amortized time complexity of $ O(1) $ for insertions over time, despite occasional expensive operations [T2].

### 4) Describe about Order of Growth with time function.

**Order of Growth**: The order of growth describes how the running time or space requirements of an algorithm increase as the size of the input data increases. It is often expressed using asymptotic notation. 

For example:
- **Constant Time**: $ O(1) $ - The running time does not change with the input size.
- **Linear Time**: $ O(n) $ - The running time increases linearly with the input size.
- **Quadratic Time**: $ O(n^2) $ - The running time increases quadratically with the input size.
- **Exponential Time**: $ O(2^n) $ - The running time doubles with each additional input element.

Understanding the order of growth helps in predicting the scalability and efficiency of algorithms as the input size grows [T6].

### 5) How the performance can be analyzed? Explain with the example.

**Performance Analysis**: The performance of an algorithm can be analyzed through various metrics, primarily focusing on time complexity and space complexity. 

To analyze performance:
1. **Identify the Input Size**: Determine how the size of the input affects the algorithm's performance.
2. **Count the Basic Operations**: Identify the fundamental operations that contribute to the running time.
3. **Use Asymptotic Notation**: Classify the algorithm using Big-O, Big-Omega, or Big-Theta notations to express its time complexity.

**Example**: Consider a simple algorithm that sums the elements of an array:
```pseudo
Algorithm sum(A, n)
{
    s = 0;
    for i = 1 to n do
        s = s + A[i];
    return s;
}
```
In this case, the basic operation is the addition, which occurs $ n $ times. Therefore, the time complexity is $ O(n) $. The space complexity is $ O(1) $ since it uses a constant amount of space for the variable $ s $ regardless of the input size [T3], [T5]. 

This analysis helps in understanding how the algorithm will perform as the input size increases, guiding decisions on algorithm selection and optimization.