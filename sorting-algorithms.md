# Sorting Algorithms
Used to sort linear data structures

## Quadratic Sorts
- [Bubble Sort](#bubble-sort)
- [Selection Sort](#selection-sort)
- [Insertion Sort](#insertion-sort)
- [Merge Sort] (#merge-sort)

Worst case time complexity is O(n^2)

They all iterate the list for each item.
The inner loop iterates to compare current item with all others, and changes the position of current item 
in order to bring the list to a sorted form with each iteration.

### Bubble Sort
- Iterate through the array for each item on the array
- For each iteration, go through each element, and swap with its next element if needed.
- N * N loop so worst case is O(n^2), best case is O(n) because if in the first iteration there were no swap that means it is sorted

Example in [go playground](https://go.dev/play/p/9uZs4MTrBoA)
```go
// using a while loop
func bubbleSortWhileLoop(arr []int) {
	done := false
	for done == false {
		fmt.Printf("starting iteration: %v\n", arr)
		done = true
		i := 0
		for i < len(arr)-1 {
			if arr[i] > arr[i+1] {
				arr[i+1], arr[i] = arr[i], arr[i+1]
				done = false
				fmt.Printf("doing a swap: %v", arr)
			}
			i++
		}
		fmt.Printf("\nending iteration: %v\n\n", arr)
	}
}

// using two for loops
// advantage of this is every incrementing iteration we skip the last element as we know it is already sorted
func bubbleSortForLoop(arr []int) {
	i := 0
	for i < len(arr)-1 {
		fmt.Printf("starting iteration: %v\n", arr)
		j := 0
		for j < len(arr)-1-i {
			if arr[j] > arr[j+1] {
				arr[j+1], arr[j] = arr[j], arr[j+1]
				fmt.Printf("doing a swap: %v", arr)
			}
			j++
		}
		i++
		fmt.Printf("\nending iteration: %v\n\n", arr)
	}
}
```

### Selection Sort

- iterate for each item in the array incrementing from 0th index to the end
- for each index position find what is the minimum and swap
- as we progress through each iteration the left side of the array starts getting sorted, as opposed to bubble sort where the right side gets sorted first
- the worst case, and best case both are O(n^2) as until we get to the end of the loop there is no way to know the minimum until we traverse the entire list

Example in [go playground](https://go.dev/play/p/l6kmiYM_Ag-)

```go
func selectionSort(arr []int) {
	i := 0
	for i < len(arr)-1 {
		fmt.Printf("\n\nstarting iteration: %v", arr)
		minIndex := i
		j := i + 1
		for j <= len(arr)-1 {
			fmt.Printf("\ntrying to find iteration: %d-%d", i, j)
			if arr[j] < arr[minIndex] {
				minIndex = j
				fmt.Printf("\nfound new minimum %v...  ", minIndex)
			}
			j++
		}
		arr[minIndex], arr[i] = arr[i], arr[minIndex]
		fmt.Printf("\nending iteration: %v", arr)
		i++
	}
}
```

### Insertion Sort

- iterate for each item in the array incrementing from 1st index to the end, we assume first item is sorted
- for each index position compare it with all the elements to the left
	- **until** an element smaller than it is found or we reach the start of the list, pushing each element before it 1 place to the right
	- when we find a smaller element we stop and place this right after the small element.
- the worst case, is O(n^2) and best case is O(n) as until we get to the end of the loop there is no way to know the minimum until we traverse the entire list

Example in [go playground](https://go.dev/play/p/iSB5rVxHwHO)

```go
func insertionSort(arr []int) {
	for k := 1; k < len(arr); k++ {
		temp := arr[k]
		prev := k - 1
		innerCount := 0
		for prev >= 0 && temp < arr[prev] {
			innerCount++
			fmt.Printf("inner count: %v\n", innerCount)
			arr[prev+1] = arr[prev]
			prev -= 1
		}

		arr[prev+1] = temp
		fmt.Printf("%v\n", arr)
	}
}
```

### Merge Sort
- divide and conquer algorithm, uses recursion
- recursively divides the array by 2 until we are left with 1 item in each array. 
- Then sorts them to get two sorted arrays. Then merges these sorted arrays into a new sorted array.
- best and worst case is O(n * log(n))

#### Why n * log(n)

https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/analysis-of-merge-sort
