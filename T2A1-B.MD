# T2A1-B_workbook
### Q1. Identify and explain the workings of TWO sorting algorithms and discuss and compare their performance/efficiency (i.e. Big O)
<hr>

Sorting algorithms in computer science used to manage data by sorting it in a specified order. Commonly used sorting algorithem are Bubble sort, Quick sort, Merge sortm insertion sort, Selection sort, etc.. Today the two sorting algorithm we will disscuss are Bubble sort and Merge sort.

### Bubble Sort
The Bubble sort algorithm is a very basic algorithm. Basically it iterates over each element of the array and compares it to its neighbors, then swaps the elements if they are not in order, repeat again until no swaping needed. The Big O complexity of Bubble sort is O(n<sup>2</sup>).
![](./pic/Bubble.png)
Example in ruby:
```ruby
def bubble_sort(array)
    len = array.length
    swapped = true
    while swap do
      swapped = false
      (len - 1).times do |a|
        if array[a] > array[a + 1]
          array[x], array[a + 1] = array[a + 1], array[a]
      swapped = true
        end
      end
    end 
    return array
end

pp bubble_sort([7,6,4,3])
# => [3,4,6,7]
```

### Merge Sort

Merge sort algorithm is another algorithm that decomposes an array into two or more subarrays, then sorts each subarray individually, and then merges all subarrays into a single sorted array. Merge sort Big O complexity is O(n logn).
![](./pic/Merge.png)

Example in ruby:
```ruby
def merge_sort(array)
  if array.length <= 1
    return array
  end

  array_size = array.length
  middle = (array.length / 2).round

  left_side = array[0...middle]
  right_side = array[middle...array_size]

  sorted_left = merge_sort(left_side)
  sorted_right = merge_sort(right_side)

  merge(array, sorted_left, sorted_right)

  return array
end

def merge(array, sorted_left, sorted_right)
  left_size = sorted_left.length
  right_size = sorted_right.length

  array_pointer = 0
  left_pointer = 0
  right_pointer = 0

  while left_pointer < left_size && right_pointer < right_size
    if sorted_left[left_pointer] < sorted_right[right_pointer]
      array[array_pointer] = sorted_left[left_pointer]
      left_pointer += 1
    else
      array[array_pointer] = sorted_right[right_pointer]
      right_pointer += 1
    end
    array_pointer += 1
  end

  while left_pointer < left_size
      array[array_pointer] = sorted_left[left_pointer]
      left_pointer += 1
      array_pointer += 1
  end

  while right_pointer < right_size
     array[array_pointer] = sorted_right[right_pointer]
     right_pointer += 1
     array_pointer += 1
  end

  return array
end

pp merge_sort([5,2,4,7,1,3,2,6])
# => [1,2,3,4,5,6,7]
```

Compare these two algorithms, the Bubble algorithm complexity is ```O(n<sup>2</sup>)```, it's sample and used for the small amount of data. The Merge sort algorithm complexity is``` O(n logn)```, it's more effective for the large amount of data.

References  
1. Andrew S.(16/07/2021), Medium, Bubble Sort, viewed 19 Feb 2022, https://medium.com/austins-software-engineering-journey/bubble-sort-b2f0d63e38f7
2. Megan(15/04/2020), DEV, Merge Sort in Ruby, viewed 19 Feb 2022, https://dev.to/mwong068/merge-sort-in-ruby-28n1
3. Gupta V.(16/07/2021), Medium, Visualizing, Designing, and Analyzing the Merge Sort Algorithm., viewed 19 Feb 2022, https://levelup.gitconnected.com/visualizing-designing-and-analyzing-the-merge-sort-algorithm-cf17e3f0371f

### Identify and explain the workings of TWO search algorithms and discuss and compare their performance/efficiency (i.e. Big O)
<hr>

Search algrithoms is an algorithm which solves a search problem. It can be classified into two types, which are swquential search and Interval search. Two search algorithms we will disscuss are Linear Search and Binary Search. 

### Linear Search

Linear search is a kind of sequential search that works by checking every element of an array in a list without skipping any elements. The Big O complexity of Linear search is O(n).

![](./pic/Linear.png)
Example in ruby:
```ruby
def linear_search(target, array)
  counter = 0
  while counter < array.length
    if array[counter] == target
      return counter
    else
      counter += 1
    end
  end
  return nil
end

pp linear_search(20, [10,50,30,70,80,60,20,90,40])
# => 6
```

### Binary Search

Binary search is a kind of interval search that can only find the target element's position in a sorted array. It works by 3 steps:
1. Compare the target element and the middle element of the array.
2. If the middle element is larger than the target element, only the right half of the array is checked. If the middle element is smaller than the target element, only the left half of the array is checked.
3. Repeat step 2 until the array can not be halved anymore, or find the position.

The Big O complexity of Binary search is O(log n).

![](./pic/Binary.png)
Example in ruby:
```ruby
def binary_search(target, array)
  low = 0
  high = array.length - 1
  while low <= high
    mid = (low + high) / 2
    if target > array[mid]
      low = mid + 1
    elsif target < array[mid]
      high = mid - 1
    else
      return mid
    end
  end
end

pp binary_search(23, [2,5,8,12,16,23,38,56,72,91])
# => 6
```

References
1. Andrew S.(11/05/2017), Medium, Binary Search Implementation in Ruby, viewed 19 Feb 2022, https://medium.com/@andrewsouthard1/binary-search-implementation-in-ruby-9636a4bf373c
2. 27/01/2020, FreeCodeCamp, Linear Search Explained, viewed 19 Feb 2022, https://www.freecodecamp.org/news/linear-search/
3. 29/11/2021, GeeksforGeeks, Searching Algorithms, viewed 19 Feb 2022,https://www.geeksforgeeks.org/searching-algorithms/
