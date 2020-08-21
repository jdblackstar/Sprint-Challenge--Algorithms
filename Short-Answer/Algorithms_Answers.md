#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a) This snippet has O(n) runtime because there is a while loop iterating based on the length of n


b) O(n)^2 (quadratic) runtime. There is a nested loop situation. I initially thought this snippet had a O(n log n) runtime, but I think that's false because we aren't having or dividing the array on each iteration.


c) This snippet has a linear runtime (O(n)) because the recursion is iterating by 1, so it's linerally related to len(bunnies)

## Exercise II


Well the brute force approach here would be to start at the first floor, presumably floor[0], and go up one floor, drop an egg, and continue until you drop an egg and it breaks. The first floor where this happens is f because we know that an egg dropped off floor >= f will break. The problem with this approach though is that it has 0(n) runtime and does not minimize number of dropped eggs (although it does minimize number of broken eggs, as only one egg will be broken using this approach). For example, if f = 99 on a 100-story building, we would drop 98 eggs and break 1.

Since we know the floors are sequential/sorted, I'm thinking a binary search could work better. Assuming we know len(n), then we can start by going to the middle floor.

Let's say we have a 7-story building, with floors 0-6. If we go to the middle floor (3), then we drop an egg and see what happens.

If the egg breaks, then it means we may be at f already, or we could be above it, but either way, we can eliminate any floors above middle, so we'll introduce O(log n) (logarithmic) runtime complexity to our process. In this situation where the egg broke, we still need to do the process again because we still might be above f. The difference though is that we will not need to simply go one floor at a time, but we can find a new middle from the remaining floors and drop another egg.

On the flip side, if the egg does not break, then we know middle is not f and we know we need to go higher. But using binary search algorithm, we can also eliminate all rows beneath us because we know they cannot be f, again using O(log n) runtime. We can then find the middle of the remaining floors above us, and repeat the process.

Using this binary search approach would be far more efficient in the 100-story building case because we are greatly reducing the amount of dropped eggs.