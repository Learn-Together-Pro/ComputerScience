# :chart_with_upwards_trend: Amortized Analysis Concepts

##### Amortized Analysis

Amortized analysis is a strategy for understanding the time complexity of algorithms, particularly when a simple worst-case or average-case analysis might be either difficult or misleading.

It helps in determining how an algorithm will perform in practice. There are three common methods used for amortized analysis: the aggregate method, the accounting method, and the potential method. Let's understand the essence of each and see what distinguishes them.

##### Amortized Analysis Methods:

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
