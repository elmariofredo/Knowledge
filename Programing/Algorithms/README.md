# Algorithm

Is step-by-step procedure for calculations.

References:
  https://en.wikipedia.org/wiki/Algorithm
  http://www.comp.nus.edu.sg/~stevenha/visualization/index.html

##❯ Sorting

Sorting list of items

References: http://www.comp.nus.edu.sg/~stevenha/visualization/sorting.html

###❯ Bubble Sort

Sorting by walking thru list and swapping each two items according to desired sort method, which is not really performant, but doesn't use any additional memory.

Example:

```ruby
def bubble_sort(array)
  n = array.length
  loop do
    swapped = false

    (n-1).times do |i|
      if array[i] > array[i+1]
        array[i], array[i+1] = array[i+1], array[i]
        swapped = true
      end
    end

    break if not swapped
  end

  array
end
```

###❯ Merge Sort

Dividing array into parts and re-collect each part according to sorting algorithm, than do the same between each part.

References:
  https://en.wikipedia.org/wiki/Merge_sort

###❯ Radix Sort

Non comparable algorithm, which is sorting byt moving each item by it's Least Significant Digit to [0,1,2,3,4,5,6,7,8,9] buckets and them recreating array based on these buckets. This process is repeated till all digits are processed. There is also MSD which is bit more complicated. It's quite performant in comparison to copare algorithms but it depends on number of buckets(keys) and digits.

References:
  https://en.wikipedia.org/wiki/Radix_sort
  https://www.youtube.com/watch?v=dHeTp6hO71U
