# Sorting Algorithms
Used to sort linear data structures

## In place sorting
does not take additional space but time complexity is worst case O(n^2)

### Bubble Sort
- Iterate through the array for each item on the array
- For each iteration, go through each element, and swap with its next element if needed.
- N * N loop so worst case is O(n^2)

Example in go (https://go.dev/play/p/9uZs4MTrBoA)
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

### Insertion Sort
### Selection Sort
