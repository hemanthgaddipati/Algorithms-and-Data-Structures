
# 1. INSERTION SORT:
Insertion sort is a simple sorting algorithm that works similar to the way you sort playing cards in your hands. The array is virtually split into a sorted and an unsorted part. Values from the unsorted part are picked and placed at the correct position in the sorted part.

Algorithm: To sort an array of size n using Insertion Sort: 
    1: Iterate from array[0] to array[n] over the array. 
    2: Compare the current element to its most recent left element. 
    3: If the current element is smaller than its immediate left element then compare it with the elements from left to 0. Move the greater elements one position to the right.

Time Complexity: O(n*2) for large arrays and O(n) for sorted arrays.

Boundary Cases: Insertion sort takes maximum time to sort if elements are sorted in reverse order. And it takes minimum time O(n) when elements are already sorted.

Uses: Insertion sort is used when number of elements is small. It can also be useful when input array is almost sorted, only few elements are misplaced in complete big array.


# 2. MERGE SORT
Merge sort is the sorting technique which based on the divide and conquer technique. Merge sort first divides the array into equal halves. Each sub array of size n/2 is sorted in a recursive manner in O(log(n)) time and then combines them in a sorted manner.

Algorithm:
    1: Find the middle point to divide the array into two halves
    2: Call merge Sort function for first half: Call merge Sort (array, 1, m)
    3: Call merge Sort for second half: Call merge Sort (array, m+1, r)
    4: Merge two halves sorted in step 2 and 3: Call merge (array, l, m, r)

Time Complexity: Ο(n*log(n)) for best, average and worst cases.

Uses: Merge Sort is useful for sorting linked lists in Ο(n*log(n)) time.


# 3. HEAP SORT
Heap sort is a comparison-based sorting technique whose structure is of Tree type. The tree is based on Binary heap data structure. This sorting technique is similar to selection sort where I first find the maximum element and place the maximum element at the end. I repeat the heapify process for remaining elements.

Algorithm:
    1: Build a max heap from the input data. 
    2: At this point, the largest item is stored at the root of the heap. Replace it with the last item of the heap followed by reducing the size of heap by 1. Finally, heapify the root of the tree. 
    3: Repeat step 2 while size of heap is greater than 1.

Time Complexity: The Running time for heapify operation takes O(log(n)) which is the height of the binary tree. After that, a sorted array is created by repeatedly removing the largest element from the heap and adding the element to the array. In this way, Heapsort takes Ο(n*log(n)) time.

Uses: Priority Queues, Order Statistics


# 4. QUICK SORT
Quicksort is a Divide and Conquer algorithm. It picks an element as pivot and partitions the given array around the picked pivot. There are many different versions of quicksort that pick pivot in different ways such as Always picking first element as pivot, always pick last element as pivot, Pick a random element as pivot, Pick median as pivot. The key process in quicksort is partition (). Target of partitions is, given an array and an element x of array as pivot, put x at its correct position in sorted array and put all smaller elements (smaller than x) before x, and put all greater elements (greater than x) after x. All this should be done in linear time.

Algorithm:
    /* low --> Starting index, high --> Ending index */
    quicksort(array[], low, high){if (low < high) {/* pi is partitioning index, array[pi] is now at right place */ pi = partition(array, low, high); quicksort(array, low, pi - 1); // Before pi quicksort (array, pi + 1, high); // After pi}}

Time Complexity: O(n^2) is the worst case and O(N*log(n)) is the average case complexity.

Uses: Quick Sort is a cache friendly sorting algorithm as it has good locality of reference when used for arrays.

# 5. MODIFIED QUICK SORT
I used median-of-three as pivot in Modified Quick sort. Which means, in this algorithm, I can pick the pivot by taking the median of left most, middle and the right most elements from the array. Compare three elements and swap these elements if necessary. If the input size is less than or equal to 15, Insertion sort algorithm is used.


## Results:

Function to generate array of random numbers for a given range “n”.
Executing for shuffled Input:
Executing for Sorted input:
Executing for Reversely Sorted input:
ANALYSIS FOR SHUFFLED INPUT: (Time in Seconds)
Len(array)

Insertion Sort, Merge Sort, Heap Sort, Quick Sort, Modified Quick Sort run times for various lengths of inputs in that order.....
# 1000
    0.08133721351623535
    0.008001327514648438
    0.008000612258911133
    0.0030663013458251953
    0.008000612258911133
# 2000
    0.2960543632507324
    0.01600170135498047
    0.01598334312438965
    0.008000373840332031
    0.01602005958557129
# 3000
    0.7516045570373535
    0.02401876449584961
    0.03998589515686035
    0.007996559143066406
    0.007983684539794922
# 4000
    1.2575297355651855
    0.03200364112854004
    0.03998541831970215
    0.015999555587768555
    0.016002178192138672
# 5000
    1.8544583320617676
    0.04802370071411133
    0.047986507415771484
    0.015982866287231445
    0.016000986099243164
# 10000
    6.502464532852173
    0.06249356269836426
    0.07813596725463867
    0.048005104064941406
    0.015613794326782227
# 20000
    18.00629734992981
    0.14401602745056152
    0.16801834106445312
    0.04687905311584473
    0.04800534248352051
# 30000
    40.652886390686035
    0.24803924560546875
    0.24802756309509277
    0.09374856948852539
    0.08000850677490234
#40000
    79.38648629188538
    0.41416168212890625
    0.3279118537902832
    0.12801313400268555
    0.16954922676086426
# 50000
    136.04107475280762
    0.5430471897125244
    0.472414493560791
    0.16002917289733887
    0.15645718574523926

Observations:
• The quick sort algorithm running time depends on the selection of pivot in the given random data. If pivot is around the median value, less time is taken, or else algorithm takes more time.
• In our case modified quick sort took more time as the size of the input increases.
• Time taken by Insertion Sort also increased as the input size increases.
• Time taken by Merge Sort and heap sort is less if the input is random data.
