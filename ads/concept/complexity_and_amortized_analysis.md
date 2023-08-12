# :chart_with_upwards_trend: Complexity and Amortized Analysis Concepts

##### Complexity Analysis

Complexity analysis is used to describe how the performance (usually the running time or space usage) of an algorithm or data structure scales with the size of the input.

It's concerned with general trends, typically in the worst-case, average-case, or best-case scenarios.

Measurement: It characterizes algorithms using Big O notation (or related notations like Θ, Ω, etc.), describing an upper or lower bound on growth as the size of the input grows.

Applicability: Complexity analysis is applied to all types of algorithms and functions, from single operations to complete algorithms, regardless of specific sequences of operations.

Examples: The time complexity of a quick sort is O(nlogn) on average, and the space complexity of a breadth-first search is O(∣V∣+∣E∣), where V and E are the set of vertices and edges in the graph.

##### Master Theorem

The Master Theorem provides a way to analyze the time complexity of recursive algorithms, specifically divide-and-conquer algorithms.

It's a handy tool for quickly determining the running time of such algorithms without having to solve the recurrence relations manually. Divide-and-conquer algorithms typically divide the problem into smaller subproblems, recursively solve the subproblems, and combine the solutions to solve the original problem. A common way to express the time complexity of a divide-and-conquer algorithm is through a recurrence relation.

It's worth noting that the Master Theorem doesn't apply to all recurrence relations. If the given recurrence doesn't fit the form, or if none of the three cases apply, other methods must be used to analyze the algorithm's time complexity.

The Master Theorem applies to recurrence relations of the following form:

T(n)=a⋅T(nb)+f(n)

Here:

- n is the size of the problem.
- a is the number of subproblems.
- b>1 is the factor by which the problem size is divided at each recursion level.
- f(n) is the time to create the subproblems and combine their results, i.e., the time - taken by the non-recursive part of the algorithm.

The Master Theorem provides three cases that cover different relationships between the functions involved, and each case gives a formula for the overall time complexity of the algorithm:

- Case 1: If f(n)=O(nc) where c<logb​a, then T(n)=Θ(nlogb​a).
- Case 2: If f(n)=Θ(nlogb​a), then T(n)=Θ(nlogb​alogn).
- Case 3: If f(n)=Ω(nc)f(n)=Ω(nc) where c>logb​a, and if af(bn​)≤kf(n) for some constant k<1k<1 and sufficiently large nn, then T(n)=Θ(f(n)).

These three cases cover different ways in which the time complexity of the recursive and non-recursive parts of the algorithm can relate to each other, allowing for a straightforward determination of the overall time complexity in a variety of common situations.

##### Amortized Analysis

Amortized analysis is a strategy for understanding the time complexity of algorithms, particularly when a simple worst-case or average-case analysis might be either difficult or misleading.

It helps in determining how an algorithm will perform in practice. There are three common methods used for amortized analysis: the aggregate method, the accounting method, and the potential method. Let's understand the essence of each and see what distinguishes them.

Measurement: It gives a more nuanced view, often applicable to data structures that sometimes have expensive operations. The amortized cost provides an averaged, per-operation cost over a sequence, ensuring that in practice, the data structure won't be inefficient.

Applicability: Amortized analysis is often applied to data structures, particularly when individual operations' cost can vary widely, and you want to understand the long-term behavior.

Examples: The amortized time complexity of adding an element to a dynamic array (that doubles in size when full) is O(1), even though individual operations might sometimes be more costly.

##### Complexity Analysis vs Amortized Analysis

Complexity analysis and amortized analysis are both techniques used to understand the performance of algorithms, but they focus on different aspects and are used in different contexts.

Complexity analysis provides a high-level understanding of how an algorithm scales, often considering the worst-case scenario.

Amortized analysis gives a more refined view of performance over a sequence of operations, averaging out the highs and lows to provide a more realistic expectation of how an algorithm or data structure performs in practice.

##### Amortized Analysis Methods

- Aggregate
- Accounting
- Potential

##### Amortized Analysis Method: Aggregate Method

Essence: This method sums the costs over the entire sequence of operations and takes the average. It often demonstrates a guarantee that no sequence of n operations can be "too expensive."

Example: If you have a sequence of operations where most are cheap but occasionally one is expensive, the aggregate method helps understand the averaged cost across the entire sequence.

##### Amortized Analysis Method: Accounting Method ~ Banker's Method

Essence: This method uses a fictional "credit" system where you "charge" more for some operations so that you can "pay" for others that might exceed their actual costs. The idea is to prove that the total credit never goes negative.

Example: In a dynamic array implementation, you might "charge" a little extra for insertion and "save" that to pay for the eventual resizing of the array.

##### Amortized Analysis Method: Potential Method

Essence: The potential method uses a carefully constructed "potential function" that maps the state of the data structure to a real number representing "potential energy" or "stored work." The changes in potential between consecutive operations pay for the actual cost of the operations.

Example: For a dynamic table operation, the potential might be proportional to the difference between the number of items and the size of the allocated array.

##### Amortized Analysis Methods Differences

Conceptual Framework: Aggregate looks at the whole sequence and takes an average, Accounting utilizes a credit system, and Potential relies on a mathematical function mapping states to "energy."

Granularity: Aggregate is often coarser and works with the entire sequence, whereas the other two methods look at the individual transitions between operations.

Flexibility: The Potential Method is often more flexible and powerful but can be more complex to construct and justify, whereas the Aggregate Method is simpler but may be less insightful for some data structures.

Use Cases: Accounting is often used when overcharging some operations to pay for others, Aggregate is applied for averaging the cost over a sequence, and Potential is applied when a careful construction of a potential function is suitable to represent the state of the operation.

Overall, the selection of the method depends on the specific algorithm or data structure being analyzed, and the particular insights or guarantees one wants to achieve. Different methods might be more suitable for different scenarios.
