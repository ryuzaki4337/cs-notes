- Selection Sort:
    - Selection Sort is a comparison-based sorting algorithm. It sorts by repeatedly selecting the smallest (or largest) element from the unsorted portion and swapping it with the first unsorted element.
        - Find the smallest element and swap it with the first element. This way we get the smallest element at its correct position.
        - Then find the smallest among remaining elements (or second smallest) and swap it with the second element.
        - We keep doing this until we get all elements moved to correct position.

    - Selection sort can handle duplicate elements effectively. It correctly places all elements, including duplicates, in sorted order. However, standard selection sort is not stable, so it does not guarantee preservation of the relative order of equal elements.

    - Selection sort doesn’t check if the array is already sorted—it always performs O(n2) comparisons because the algorithm doesn’t adapt to sorted inputs. While no swaps may occur if the array is sorted, the comparisons in the inner loop are still executed, making it inefficient for pre-sorted data.

    - Selection sort works in-place and uses O(1) extra memory. For systems with strict memory limitations, it is a viable choice.
    
    - For small arrays (e.g., fewer than 10 elements), the simplicity of selection sort can outweigh its inefficiency. The overhead of more complex algorithms, like merge sort or quicksort, might not be justified. Example: Sorting [5, 2, 1] in embedded systems with limited RAM can efficiently use selection sort.

    - Both insertion sort and selection sort have O(n^2) worst-case time complexity. However, insertion sort can outperform selection sort for nearly sorted arrays because it minimizes shifts, while selection sort always performs n−1 comparisons in the inner loop, regardless of the array's state. Swaps vs. Shifts: Selection sort minimizes swaps (n−1 swaps in total), making it suitable for situations where swap costs are high (e.g., flash memory). Insertion sort involves more shifts, especially for large unsorted portions. Example: For an array like [2, 3, 4, 5, 1], insertion sort will quickly sort it with fewer operations because most elements are already in place. In contrast, selection sort performs the same number of comparisons regardless of the initial order, making it less efficient in this case.

- Bubble Sort:
    - The bubble sort algorithm sorts an array by repeatedly swapping adjacent elements if they are in the wrong order. The largest elements "bubble" to the end of the array with each pass.

    -  This algorithm is not efficient for large data sets as its average and worst-case time complexity are quite high.

    - Sorts the array using multiple passes. After the first pass, the maximum goes to end (its correct position). Same way, after second pass, the second largest goes to second last position and so on.
    
    - In every pass, process only those that have already not moved to correct position. After k passes, the largest k must have been moved to the last k positions.
    
    - In a pass, we consider remaining elements and compare all adjacent and swap if larger element is before a smaller element. If we keep doing this, we get the largest (among the remaining elements) at its correct position.

- Insertion Sort:
    - Insertion sort builds a sorted array one element at a time by repeatedly picking the next element and inserting it into its correct position within the already sorted part of the array.

    - Insertion sort is a simple sorting algorithm that works by iteratively inserting each element of an unsorted list into its correct position in a sorted portion of the list. It is like sorting playing cards in your hands. You split the cards into two groups: the sorted cards and the unsorted cards. Then, you pick a card from the unsorted group and put it in the right place in the sorted group.

    - Approach:
        - In each iteration, select an element from the unsorted part of the array using an outer loop.
        - Place this element in its correct position within the sorted part of the array.
        - Use an inner loop to shift the remaining elements as necessary to accommodate the selected element. This involves shifting the elements by one place until the selected element can be placed at its correct position.
        - Continue this process until the entire array is sorted.

    - Time Complexity
        - Best case: O(n), If the list is already sorted, where n is the number of elements in the list.
        - Average case: O(n2), If the list is randomly ordered
        - Worst case: O(n2), If the list is in reverse order
    
    - Space Complexity
        - Auxiliary Space: O(1), Insertion sort requires O(1) additional space, making it a space-efficient sorting algorithm.

    - Stable sorting algorithm.

- Merge Sort:

    - Merge Sort is a powerful sorting algorithm that follows the divide-and-conquer approach. The array is divided into two equal halves until each sub-array contains only one element. Each pair of smaller sorted arrays is then merged into a larger sorted array.

    - The algorithm consists of two main functions:
        - merge():This function merges the two halves of the array, assuming both parts are already sorted.
        - mergeSort():This function divides the array into 2 parts: low to mid and mid+1 to high where, low is the leftmost index of the array, high is the rightmost index of the array, and mid is the middle index of the array.
        
        - By repeating these steps recursively, Merge Sort efficiently sorts the entire array.

    - Approach:
        - To implement Merge Sort, we will create two functions: mergeSort() and merge().

        - mergeSort(arr[], low, high):
            - Divide the Array: Split the given array into two halves by splitting the range. For any range from low to high, the splits will be low to mid and mid+1 to high, where mid = (low + high) / 2. This process continues until the range size is 1.

            - Recursive Division: In mergeSort(), divide the array around the middle index by making recursive calls: mergeSort(arr, low, mid) for the left half and mergeSort(arr, mid+1, high) for the right half. Here, low is the leftmost index, high is the rightmost index, and mid is the middle index of the array.

            - Base Case: To complete the recursive function, define the base case. The recursion ends when the array has only one element left, meaning low and high are the same, pointing to a single element. If low >= high, the function returns.

        - merge(arr[], low, mid, high):
            - Use a temporary array to store the elements of the two sorted halves after merging. The range of the left half is from low to mid and the range of the right half is from mid+1 to high.

            - Use two pointers, left starting from low and right starting from mid+1. Using a while loop (while left <= mid && right <= high), compare the elements from each half and insert the smaller one into the temporary array. After the loop, any leftover elements in both halves are copied into the temporary array.

            - Transfer the elements from the temporary array back to the original array in the range low to high.

    - Time Complexity: O(nlogn). At each step, we divide the whole array, which takes logn steps, and we assume n steps are taken to sort the array. So, the overall time complexity is nlogn. This is the complexity in best, average and worst case.

    - Space Complexity: O(n). We are using a temporary array to store elements in sorted order.

    - Merge sort is not an in-place sorting algorithm, which means it requires additional memory to store the sorted data.

    - Merge Sort is Slower than QuickSort in general as QuickSort is more cache friendly because it works in-place.