# Complete Intro Computer Science

## 1. Algorithm Analysis

https://btholt.github.io/complete-intro-to-computer-science/

### 1.1 Big O Time Complexity

- how efficient an algorithm is from broad perspective / not getting into details
- we care only if difference in time is large 

```
3x² + x + 1
```

x = 5  then 1st term (3x2) - 75
x = 1  then 1st term 5 
here the first term caries most of the load 

Big O - ignore the little parts and concentrate on big parts
for our equation 
`3x² + x + 1`
O(n²)
we look at the biggest term which carry the biggest weight 


question what is output when array has few and thousands elements 

-  ? how many instructions we pass to cpu 
   `var answer =[]`
   `return answer` 
   those 2 are called twice 
   for loop depends on length of input 
   if input is 1  => for loop only once 
   if inpus is 1M => milion times (taking cpu)

```js
function crossAdd(input) {
  var answer = [];
  for (var i = 0; i < input.length; i++) {
    var goingUp = input[i];
    var goingDown = input[input.length - 1 - i];
    answer.push(goingUp + goingDown);
  }
  return answer;
}
```

complexity is O(n) - where n is length of array 
what we do in foor loop is  like 3x (coefficient)

Linear search in array 

 - we look for needle in our array 
   **big o for this loop** 

  > O(n) -> it could be the last element / it could be the first item 

```js
function find(needle, haystack) {
  for (var i = 0; i < haystack.length; i++) {
    if (haystack[i] == needle) return true;
  }
}
```

it could be Best case scenario when n is first item
average - in the middle
worst case - the last item in array 

if we have nested loops :
 O(n²) - quadratic
we are going to make array with array 
if we pass 10 -> 100 

```js
function makeTuples(input) {
  var answer = [];
  for (var i = 0; i < input.length; i++) {
    for (var j = 0; j < input.length; j++) {
      answer.push([input[i], input[j]]);
    }
  }
  return answer;
}
```

A loop inside of a loop inside of a loop would likewise be O(n³).

If we have no loops and just do something and exit/return, then it's said we're doing it in constant time, or O(1).

```js
function getMiddleOfArray(array) {
  return array[Math.floor(array.length / 2)];
}
```

This would be O(1) because no matter how long the array is, this still takes the same amount of time to do.

there is another line 
We'll get more into it later, but you can also have O(log n) if a code employs a divide-and-conquer strategy (often recursive,) meaning as you add more terms, the increases in time as you add input diminishes. 

### 1.2 Why use Big O

to measure speed 

-  comment system for website
-  with sorting and filtering algorithms 
-  **what is right big o for comments ?**
   -> do not spend time on things that do not matter 
   -> we can not judge algo based on speed only 
   -> maintanable & readiness 

-  computional complexity : 
   if we give more inputs  / how many more CPU cycles it is gonna take ? 

### 1.3 Spatial Complexity

How much ram or hard disk will take ?

**Linear** O(n)
we have algorithm that for every item in array - needs to create another array
 for an array of length 10, our algorithm will create 10 arrays
  for an array of 100 -  100 extra array 
This would be O(n) in terms of its spatial complexity
**logarithmic**
 for every item in the array, it needed to create a diminishing amount of extra arrays.
 for an array of length 10, it'd create 7 arrays. 
 For an array of 100, it'd create 12 arrays. 
 For an array of 1000, it'd created 20 arrays. 
 This would be O(log n).

**constant**
 if we didn't create any extra arrays when we did our algorithm? We just used the same space we were given when we first started. Or if we created just 10 arrays, no matter how long the array is? This would be O(1) since it's constant no matter what. 
 Its spatial need don't increase with longer arrays.

**quadratic**
distance between zip codes

we have 10 000 zip codes -> add another 10k zip codes  > create table for new records  



### 1.4 Big O trade - Offs 

  business issues vs technical issues vs time issues 

big o could lead us to focus on something less important 

**readability and maintability is the most important**

> optimize when you need to optimize 

- use buit-in feature  rather than built onw 

**Testing ?** - keep with growing / what do you anticipate 

- we could spend thousands hours on optimization 



## 2. Iterative Sorts 

### 2.1 Bubble Sort 

- not used in production - there are better 

- **fits human mental model** - how humans sort numbers 



biggest number - bubbles to the top  and then it sorts rest of array 

 ```
[1,5,4,2,3]
 1 is bigger than 5 ? - No
 5 is bigger than 4 ? - yes, swap
[1,4,5,2,3]
5 is bigger than 2 ? - yes, swap
5 is bigger than 3 ? - yes swap
[1,4,2,3,5]
End of Array - loop again
1 > 4?  No 
4 > 2? Yes - swap
4 > 3? Yes - swap
4 > 5? No
End of array - loop again
[1,2,3,4,5]
1 > 2? no
2 > 3? no
3 > 4? no
4 > 5? no
End of array List is sorted
 ```

**Time complexity** - computation 

Best Case - sorted list On

Average Case - n2 - we have outer loop and inner loop 

Wors case - reversed list sorted list - we 



**Spatial Compleixty of this** - constant / we do not create any additional array - no 



Is this sorting algorith stable ? 

> if 2 things are equal - that they stay in the same order 

assume we are sorting by state: 

```
[{state: "CO", name: "Sarah Drasner"}, {state: "CA", name: "Shirley Wu"}, {state: "CA", name: "Scott Moss"}]
```

make sure that Shirley  stay in the place 

### 2.2 Bubble Sort example



more optimized one 

```js
function bubbleSort(arr){
  var i, j;
  var len = arr.length;

  var isSwapped = false;

  for(i =0; i < len; i++){

    isSwapped = false;

    for(j = 0; j < len; j++){
        if(arr[j] > arr[j + 1]){
          var temp = arr[j]
          arr[j] = arr[j+1];
          arr[j+1] = temp;
          isSwapped = true;
        }
    }

    // IF no two elements were swapped by inner loop, then break

    if(!isSwapped){
      break;
    }
  }

  // Print the array
  console.log(arr)
}


var arr = [243, 45, 23, 356, 3, 5346, 35, 5];
bubbleSort(arr);

```





### 2.3 Insertion sort 

better than bubble sort 



- start with array of lenght 1 (0) 

  ​	> array previous to index - 1 is sorted one - array with 1 element must be sorted 

we shift number while we iterate over : 

```
[3,2,5,4,1] 
[3] - is sorted 
[2,4,5,4,1] - is unsorted 
we take 2 and insert into sorted
2 > 3 ? - no 
move 3 to the right and insert two at index 0 
[2,3,5,4,1]
5 > 3 ? - insert after 3 
4 > 5 ? - move 5 to the right
4 > 3 ? yes - insert after 3 at index 2
[2,3,4,5,1]
1  > 5 ? - no move 5 to right 
1 > 4 ?  - move 4 to right
..
1 > 2? - move 2 to right
[1,2,3,4,5]
reached end of list - list is sorted 
```

numbers continually shifts over 

**Big O**

- Wort case scenario:

  > reversed sorted list  - we need to shift evry

- Best case scenario:

  everything sorted 

- Average

​	n2 - shuffled array



we got data from database and it is mostly sorted 



we have 100 items from array and we know that 98 is in sorted order

spatial complexity is contant - we did not create anything in memory 

```js
function insertionSort(arr) {
    for(let i = 1; i < arr.length; i++) {
        let current = arr[i];
             console.log(current);
        let j = i - 1;
        while((j > -1) && (current < arr[j])) {
            arr[j+1] = arr[j];
            j--;
        }
   
        arr[j+1] = current;
    }
    return arr;
}

let inputArr = [5, 2, 4, 6, 1, 3];
insertionSort(inputArr);
console.log(inputArr);
```



### 3. Recursion

Big problem - break into smaller problem 

Big array - break into smaller array  untill are sorted

in english Recursion is when we try define word using word themselves:

`What is seafarer?` -- `one who fares the seas`

recursive function - function call itself 

doing a loop with a function :

```js
function countTo(max, current) {
    if (current > max) return;
    console.log(current);
    countTo(max, current +1);
}
const counts = countTo(5,1); // outputting from 1-5
```

modelling version of smaller version of the problem 

**fibonnaci**- number that is defined as sum of previous 2 fibonnaci numers 

fib(3) = fib(2) + fib(1)

fib(n) = fib(n-1) + fib(n-2)



**best case ** : when we stop recursing

if we do not stop recusrion - we got stack overflows

```js
function fibonacci(n) {
  // base case
  if (n === 2 || n === 1) {
    return 1;
  } else if (n <= 0) {
    return 0;
  }

  // recursive calls
  return fibonacci(n - 1) + fibonacci(n - 2);
}
```

### 3.1 Nested Addition Exercise 

we have array  with numbers and more arrays (with numbers and arrays)

```
[1, 2, 3, 4, 5, [6, 7, 8], 9, [[10, 11], 13, [14]]]
```

```js
function nestedAdd(array) {
    let sum = 0;
    for (let i = 0; i < array.length; i++) {
      const current = array[i];
      if (Array.isArray(current)) {
        sum += nestedAdd(current);
      } else {
        sum += current;
      }
    }
    return sum;
  }
  
const result = nestedAdd([1,2,3, [1,1]]);
```

### 3.2 Merge Sort

we have big list unsorted 

- break it into 2 smaller lists 
- we have 2 smaller lists - break to smaller

eventually we are going to end up with lists of length 1 or 0 (already sorted )

we need to merge them all back into 1 sorted list ! 

**need 2 functions**

- 1) function to break down big lists into smaller lists (recursive)
  2) takes 2 **sorted** lists and return 1 **sorted**



we have 2 lists of length 1 so are sorted and we are going to merge them together 

```bash
mergeSort([1, 5, 7, 4, 2, 3, 6]) -- depth 0
```

divide : 

```
mergeSort([1, 5, 7, 4]) // mergeSort([2, 3, 6]) -- depth 1
```

divide -- go deeper

```bash
mergeSort([1,5]) // mergeSort([7,4]) -- depth 2 
```

divide -- go deeper

```bash
mergeSort([1]) // mergeSort([5]) -- depth 3
```

`[1]` and `[5]` - both are length 1 - base case - are sorted 

add 2 together  is 1 or 5 smaller ? 

 left array will be empty concat. to right

```bash
merge([1], [5]) -- depth 3 #Return sorted array [1, 5].
```

second part of the same array `depth 1 `

```bash
mergeSort([7, 4]) -- depth 2
mergeSort([7]) // mergeSort([4]) -- depth 3
merge([7], [4]) -- depth 3 # Return sorted array [4, 7]
```

is 7 or 4 smaller add to the end right array is smaller concat left array 

now concat together 2 arrays 

```bash
merge([1, 5], [4, 7]) -- depth 2
```

> 1 or 4 smaller ? add to the end `[1]`
>
> 5 or 4 smaller ? add to the end `[1,4]`
>
> 5 or 7 smaller ? add to the endd `[1,4,5]`
>
> left array is empty concat right array `[1,4,5,7]`

```text
Return sorted array [1, 4, 5, 7]
```

```bash
mergeSort([2, 3, 6]) -- depth 1
mergeSort([2, 3]) // mergeSort([6])  -- depth 2
mergeSort([2]) // mergeSort([3]) -- depth 3
merge([2], [3]) -- depth 3 # Left array is empty, concat right array. [2, 3]


merge([2, 3], [6]) -- depth 2
# Is 2 or 6 smaller? 2. Add to end. [2]
#Is 3 or 6 smaller? 3. Add to end. [2, 3]
#Left array is empty, concat right array. [2, 3, 6]
#Return sorted array 
[2, 3, 6]
```



```bash
merge([1, 4, 5, 7], [2, 3, 6]) -- depth 1
```

> is 1 or 2 smaller ? add to the end `[1]`
>
> is 4 or 2 smaller ? add to the end `[1,2]`
>
> is 4 or 3 smaller ? add to the end `[1,2,3]`
>
> is 4 or 6 smaller ? add to the end `[1,2,3,4]`
>
> is 5 or 6 smaller ? add to the end `[1,2,3,4,5]`
>
> is 7 or 6 smaller ? add to the end `[1,2,3,4,5,6,7]`



most engine use `mergeSort` 

sometimes engine call `quickSort` 

it is solid sort 

**big O**

every case is worst, best case scenario

there is no difference 

. So for merge sort all three of best, worst, and average case computational complexity the answer will be the same.



every item in array will be looked at least once `O(n)`

but 1 is never compared to 7 - we had a shortcuts 

more and more we have economies of scale - but still we need to look on every element

omputational complexity is `O(n log n)`

spatial complexity is O(n).

```js
const mergeSort = (nums) => {
    // base case
    if (nums.length < 2) {
      return nums;
    }
    const length = nums.length;
    const middle = Math.floor(length / 2);
    const left = nums.slice(0, middle);
    const right = nums.slice(middle);

    return merge(mergeSort(left), mergeSort(right));
  };
  
  const merge = (left, right) => {
    const results = [];
  
    while (left.length && right.length) {
      if (left[0] <= right[0]) {
        results.push(left.shift());
      } else {
        results.push(right.shift());
      }
    }

    return results.concat(left, right);
  };
```



## 
