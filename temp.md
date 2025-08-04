The function `function sum() {return a +b;}` as written has a problem: **where do `a` and `b` come from?**

In JavaScript, for `a` and `b` to be used inside the function, they need to be:

1. **Passed as arguments (most common and best practice):** The function takes `a` and `b` as inputs.
2. **Declared within the function's scope:** `let a = 5; let b = 3;` (but then it's not very useful for summing
*different* numbers).
3. **Globally defined:** `let a = 10; let b = 20; function sum() { return a + b; }` (generally discouraged as it makes
functions less reusable and harder to debug).

---

### What will happen with your current code?

If `a` and `b` are not defined anywhere accessible by the function, you will get a `ReferenceError`:
```
ReferenceError: a is not defined
```

If `a` and `b` *are* defined globally but, for example, `b` is `undefined` or `null`, the sum might result in `NaN` (Not
a Number) or unexpected behavior.

---

### How to make it work correctly (Common Scenarios):

#### 1. The Standard Way: Pass `a` and `b` as arguments

This is the most common and correct way to create a `sum` function that adds two specific numbers.

```javascript
function sum(a, b) {
return a + b;
}

// How to use it:
let result1 = sum(5, 3); // result1 will be 8
let result2 = sum(10, -2); // result2 will be 8
let result3 = sum(0.5, 1.5); // result3 will be 2

console.log(result1);
console.log(result2);
console.log(result3);
```

#### 2. Summing any number of arguments (Modern JavaScript with Rest Parameters)

If you want the `sum` function to be able to add two, three, four, or any number of values, you can use the rest
parameter syntax (`...`). This collects all arguments passed into an array.

```javascript
function sumMany(...numbers) {
let total = 0;
for (let i = 0; i < numbers.length; i++) { total +=numbers[i]; } return total; // A more concise way using
    Array.prototype.reduce(): // return numbers.reduce((accumulator, currentValue)=> accumulator + currentValue, 0);
    }

    // How to use it:
    console.log(sumMany(1, 2)); // Output: 3
    console.log(sumMany(1, 2, 3, 4)); // Output: 10
    console.log(sumMany(10, 20, 30, 40, 50)); // Output: 150
    console.log(sumMany()); // Output: 0 (if no arguments are passed)
    ```

    #### 3. Summing elements of an array

    If you have an array of numbers and want to sum them up:

    ```javascript
    function sumArray(numbers) {
    let total = 0;
    for (let i = 0; i < numbers.length; i++) { total +=numbers[i]; } return total; // Or, more concisely using
        Array.prototype.reduce(): // return numbers.reduce((accumulator, currentValue)=> accumulator + currentValue, 0);
        }

        // How to use it:
        let myNumbers = [10, 20, 30, 40];
        let sumOfArray = sumArray(myNumbers); // sumOfArray will be 100
        console.log(sumOfArray);

        console.log(sumArray([1, 2, 3])); // Output: 6
        ```

        ---

        **In summary, the most common and correct way to implement your `sum` function is to pass the numbers you want
        to add as arguments:**

        ```javascript
        function sum(a, b) {
        return a + b;
        }
        ```