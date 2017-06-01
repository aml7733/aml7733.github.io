---
layout: post
title:  Intro to the Big O
date:   2017-06-01 00:31:50 +0000
---


"Big-O" analysis is a way of measuring algorithm efficiency.  It's abstract and not incredibly accurate, but it works for a higher-level efficiency analysis.  Not "can we save miliseconds doing this way over that way," but more like "this way is conceptually more efficient for very large inputs."

It's best demonstrated with examples, and the following is taken from *Programming Interviews Exposed*, by Monjan, Giguere, and Kindler (p.25), translated into Ruby.  We want a function that returns the maximum value in an array of non-negative integers (of size *n*).  There are several ways to do this:



The first keeps track of the current largest value, updating as the function iterates through the array, before finally returning the stored max.

```
def compare_to_max (array)
    return nil if array.length == 0
		
		current_max = array[0]
		
		array.each do |element|
		    current_max = element if element > current_max
		end
		
		current_max
end
```



The second way compares each value to all other values, only returning the element if all other elements are less than or equal.  For the sake of clarity, I'll use nested for loops (although it's not the most efficient or pretty, it demonstrates the point).  The first iteration sets is_max to true for each element, then iterates through again to check to see if any other element is greater (if so, it resets is_max to false and breaks, allowing the first iteration to continue).  If the second iteration completes without breaking, the first iteration will stop and the function will return the element.

```
def compare_to_all (array)
    return nil if array.length == 0
		
		i = array.length - 1
		while i > 0
		    is_max = true
				
				j = 0
				while j < array.length
				    if array[j] > array[i]
						    is_max = false
								break
						end
						
				    j += 1
				end
				
				break if is_max
				
		    i -= 1
	  end
		
		array[i]
end
```


First, we figure out what the input is, and what *n* represents.  Then we construct an abstract equation for the number of operations performed by each function.  This equation is expressed in terms of n as follows: O(f(n)).

Computers are fast enough these days that small values of n are insignificant, sometimes unnoticeable.  We're only concerned with the function as n becomes very large (that is, as n approaches infinity).  In both functions there is only one input, the array being analyzed.  We can express the number of operations performed in each function with respect to the size of the array, and consider that to be n.  n = array.length, in Ruby.  

In compare_to_max, the first operation performed is the check to see if the array is empty (O(1)). It then arbitrarily sets the max value to the value of the first element of the array (O(2)).  The important bit is the iteration.  It performs a check to see if each element in the array is greater than the max value (O(2+n)), and worst case scenario, it has to change the max value each time it iterates (O(2+n+n), or O(2n + 2)).  Best case scenario, the first value is the max (never has to change the max value), and the function only runs n + 2 operations, or O(n+2).  This averages out to O((3/2)n + 2).  Lucky us, it doesn't matter what the exact formula is.  We drop all but the highest-order terms, and remove constants.  As the size of the array increases, the number of operations increases linearly, which runs in O(n) time.

In compare_to_all, we have the same n, and two iterations through the array.  However, this solution has a break once the correct number is found.  Worst case, when the max is the last element, it would run in O(n^2) time, iteration fully through the array and using the comparision operator for each element.  In the average case, when the max is in the middle, the first iteration only needs to go half way, resulting in O(1/2 * n^2)) time.  Since we ignore the constants, we generally would represent this as O(n^2) time, or polynomial time.  

It's clear that an algorithm that has linear time has significantly fewer operations than an algorithm that has polynomial time.  As n grows very large, say 10,000 elements in the array, compare_to_max would run about 10,000 operations.  compare_to_all would run about 100,000,000 operations.  At these levels, the time taken is really noticeable.
