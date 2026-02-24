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