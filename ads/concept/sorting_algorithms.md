# :chart_with_upwards_trend: Algorithms : Sorting Concepts

##### Sorting Algorithms

- Bubble Sort
- Selection Sort
- Insertion Sort
- Merge Sort
- Quick Sort
- Heap Sort
- Shell Sort
- Radix Sort
- Counting Sort
- Bucket Sort

##### Bubble Sort

Repeatedly compares adjacent elements and swaps them if they are in the wrong order.

```
[5, 3, 3, 4, 2]
[5, 3, 3, 2, 4]
[5, 3, 2, 3, 4]
[5, 2, 3, 3, 4]
[2, 3, 3, 4, 5]
```

##### Selection Sort

Finds the minimum element and places it at the start.

```
[5, 3, 3, 4, 2]
[2, 3, 3, 4, 5]
```

##### Insertion Sort

Inserts each item into its correct position.

```
[5, 3, 3, 4, 2]
[3, 5, 3, 4, 2]
[3, 3, 5, 4, 2]
[3, 3, 4, 5, 2]
[2, 3, 3, 4, 5]
```

##### Merge Sort

Divides into sublists, then merges them.

```
Divide: [5, 3, 3, 4, 2]
Merge: [2, 3, 3, 4, 5]
```

##### Quick Sort

Uses a pivot to partition elements.

```
Partition: [5, 3, 3, 4, 2]
[2, 3, 3, 4, 5]
```

##### Heap Sort

Builds a heap and extracts elements.

```
Heapify: [5, 3, 3, 4, 2]
[2, 3, 3, 4, 5]
```

##### Shell Sort

Insertion sort with a "gap."

```
[5, 3, 3, 4, 2]
[2, 3, 3, 4, 5]
```

##### Radix Sort

Sorts numbers digit by digit.

```
Units: [5, 3, 3, 4, 2]
Tens: [2, 3, 3, 4, 5]
```

##### Counting Sort

Counting sort is a non-comparison sorting algorithm that sorts elements based on their frequencies.

The algorithm is efficient when the range of values (i.e., `k`) is not significantly larger than the number of values being sorted.

##### Counting Sort: Stages

1. *Find the Maximum Value*: Identify the maximum value in the input array to determine the range of counts.
2. *Initialize Count Array*: Create an array (count array) of zeros with length one more than the maximum value.
3. *Count Occurrences*: Iterate through the input, incrementing the corresponding index in the count array for each value.
4. *Calculate Cumulative Counts*: Replace each count with the cumulative sum of the previous counts in the count array.
5. *Create Output Array*: Create a new array (output array) for the sorted values.
6. *Place Values in Output Array*: Iterate through the input, placing values in the output array using the count array, and decrementing the count array accordingly.
7. *Copy Output Array to Input Array*: If needed, copy the output array back into the input array.

##### Counting Sort: Example

*Input Array*: `[4, 2, 2, 8, 3, 3, 1]`

- *Find Maximum Value*: `max = 8`
- *Initialize Count Array*: `[0, 0, 0, 0, 0, 0, 0, 0, 0]`
- *Count Occurrences*: `[0, 1, 2, 2, 1, 0, 0, 0, 1]`
- *Calculate Cumulative Counts*: `[0, 1, 3, 5, 6, 6, 6, 6, 7]`
- *Create Output Array*: `[_, _, _, _, _, _, _]`
- *Place Values in Output Array*: `[1, 2, 2, 3, 3, 4, 8]`
- *Copy Output Array to Input Array*: `[1, 2, 2, 3, 3, 4, 8]`

##### Counting Sort: Complexity

- *Time Complexity*: `O(n + k)`
- *Space Complexity*: `O(n + k)`
- `n` ~ the number of elements,
- `k` ~ the range of the input.

##### Bucket Sort

Sorts elements into buckets.

```
Buckets: [5, 3, 3, 4, 2]
[2], [3, 3], [4], [5]
Result: [2, 3, 3, 4, 5]
```
