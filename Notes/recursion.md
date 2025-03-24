## Recursion Class Notes: 


Recursion is a programming technique where **a function calls itself to solve smaller instances of the same problem.**

It's often used to break down complex problems into simpler ones and can be aprticularly useful for problems that can be divided into similar sub-problems.



**Real Life Example:**

## Where it is used?
- Data Structures (Trees, Graphs, Linked Lists)
- Sorting Algorithm (Quick Sort, Merge Sort)
- File System Navigation (Traversal)
- Solving Puzzles and Games (Towers of Hanoi, Maze Solvers)
- Dynamick Programming 
- Parsing Expressions and Syntax Trees 
- Mathematical Computation (Factotials, Permutations)
- Backtracking Algorithms (N-Queens, Sudoku Solver)
- Artificial Intelligence (Minimax, Alpha-Beta Pruning)


## Understanding Call Stack 

Call Stack is a data structure. When a function call then all of the function call one ofter another.


**Example:**
```js
// Call Stack 

function one(){
    console.log(1)
}

function two(){
    console.log(2)
}

function three(){
    console.log(3)
}

one()
two()
three()
```

Now make it more different.

```js
// Call Stack 

function one(){
    two() // 2
    console.log(1)
}

function two(){
    three() // 3
    console.log(2)
}

function three(){
    console.log(3)
}

one() // 1
```

## Understanding Recursion

**Example of factorial:**

```js 
    // factorial(5) -> 5 * 4 * 3 * 2 * 1

    function factorial(n){
        // base case
        if (n == 0 || n == 1) return 1;

        return n * factorial(n - 1) // ei function ta jotokhon call hobe totokhon parent function run hobe
    }

    cosnole.log(factorial(5)) // first e ei function a call hobe.
```

`Note: ` We shouldn't run function infinitly, We must have to stop the functioin by using base case. 


## Factorial iterative solution

Factorial of a number means jei number ta amra bar korte chachi sai number er up to one porjonto gonfolei hoche factorial. 

**Example:** `5! = 5 * 4 * 3 * 2 * 1`
**Notes:** `0! = 1 and 1! = 0`

```js 
    function factorial(n){
        let result = 1;
        if(n == 0 || n == 1) return 1;

        for(let i = n; i >= 2; i--){
            result *= i
        }
    }

    factorial(4)
```


## Factorial Recursive solution. 

Call Stack means akta function aktar por arakta call hocche sai baperta call stack moddo die amra pai. 

```js 
function factorial(n){

    if(n == 0 || n == 1) return 1;
    // n thake ak kore combe
    return n * factorial(n - 1)
}

factorial(4)
```

<!-- Let's explain how call stack working

    fact(4)
        4 * fact(3)
            3 * fact(2)  
                2 * fact(1)



    fact(4)
        4 * fact(3) (4 * 6) == 24 our final result will be 24 return 24
            3 * fact(2)  (3 * 2) == 6 now return 6
                2 * fact(1) return 2

recursion own't count instantly at first it will perform its iteration up to lower number then it will return and multiply the value lower to upper number. And in recursion we must have to check edge case. 


call Stack.

fact(1)
fact(2)
fact(3)
fact(4)
-->


## Must Remember

- Must have a Base Case (Terminate calling of the function)

- Some sort of change in arguments during calling the recursive functions to avoid infinite loop.

- Return with caution. 


**Benefits of recursion:**
- **Simplicity:** Problems that can be naturally divided into similar sub-problems are often simpler to solve with recursion.

- **Clarity:** Recursive solutions can be more readable and easier to understand for problems that have a clear recursive structure.


**Drawbackd of recursion:**

- **Performance:** Recursive calls can lead to significant overhead, particularly if many calls are made. This can be mitigated with techniques like memoization or iterative solutions.

- **Stack Overflow:** Deep recursion may lead to stack Overflow errors if the recursion goes too deep. 


## Simple looping technique iteratively and recursively

**Recursive solution**
```js 
    function printNumberR(n){
        // base case
        if(n < 0) return 

        console.log(n) // 5-0 
        // eikhane recursive function ta loop korche up to lowest.
        printNumberR(n - 1) // jokhon lowest number e ase pochabe tokhon call stack ta call hote thakbe.

        console.log(n) // 0-5 

        // ei khanke function ta call korar somoy sobar seser thake call korche 0,1,2,3,4,5
    }

    printNumberR(5)
```

## Sum 1 to n recursively

```js 
function sum(num){
    if( num == 1) return 1

    return num += sum(num - 1)
}
```


## Pure recursion with sum of even values. 

```js 

function collectEvenValuesPure(arr){
    let result = []

    // base case
    if (arr.length == 0){
        return result
    }

    // check if the first element is even
    if (arr[0] % 2 == 0) {
        result.push(arr[0])
    }

    // recursive case 
    result = result.concat(collectEvenValuesPure(arr.slice(1)))

    return result 
}

console.log(collectEvenValuesPure([1,2,3,4,5,6,7,8]))
```


## Impure recursion with sum of even values. 

```js 
function collectEvenValuesImpure(arr, result = []){
    // base case
    if (arr.length == 0) return result;

    // check if the first elemt is even
    if(arr[0] % 2 == 0){
        result.push(arr[0])
    }

    // recursive case
    return collectEvenValuesImpure(arr.slice(1), result)
}   
```

**Impure recursion more cleaners**

```js 
function collectEvenValuesImpure(arr){
    let result = []

    function helperRecur(arr){
        // base case
        if (arr.length == 0) return result;

        // check if the fisr elem is even
        if(arr[0] % 2 == 0) result.push(arr[0])

        // recursive case
        return helperRecur(arr.slice(1))
    }

    helperRecur(arr)
    return result
}

```
Impure recursion is memory memory effecient and pure recursion is not memory effecient.
