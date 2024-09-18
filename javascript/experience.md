### Doubts and clarifications

 - **Question:** What is the ?. operator and what is it used for?

    **Answer:** The ?. operator in JavaScript is called the optional chaining operator. It allows you to safely access deeply nested object properties without having to check if each reference in the chain is valid (i.e., not null or undefined). It is used in all these scenarios:
    - **Avoid errors when accessing properties**:
    ```javascript
    let user = { name: "Alice", address: null };
    console.log(user?.address?.city); // Output: undefined (instead of throwing an error)
    ```
    - **Optional method calls**:
    ```javascript
    let user = {
      greet: () => "Hello",
    };
    console.log(user.greet?.()); // Output: Hello
    console.log(user.sayBye?.()); // Output: undefined (method doesn't exist)
    ```

    - **Optional array access**:
    ```javascript
    let arr = [1, 2, 3];
    console.log(arr?.[5]); // Output: undefined (no error even if index is out of bounds)
    ```

 - **Question:** What are backticks(``) used for in javascript?

    **Answer:** In JavaScript, the backticks (``) are used to create **template literals**, which allow for:
    - **String interpolation**: Inserting variables or expressions into strings using `${}`.
   ```javascript
   let name = "Alice";
   console.log(`Hello, ${name}!`); // Output: Hello, Alice!
   ```
    - **Multiline strings**: Writing strings that span multiple lines.
   ```javascript
   let message = `This is
   a multiline
   string.`;
   ```
    - **Expression evaluation**: You can also place expressions inside `${}`.
   ```javascript
   let a = 5, b = 10;
   console.log(`The sum is ${a + b}`); // Output: The sum is 15
   ```

### Arrow Function syntax fine details

In JavaScript arrow function syntax, the use of {} (curly braces) and () (parentheses) depends on the function's requirements:

 - When the arrow function has a single expression, you can omit {}. The expression is implicitly returned.

    ```const add = (a, b) => a + b;```

 - If the function body contains multiple statements, you must use {} to define the block.
```
 const add = (a, b) => {
    const sum = a + b;
    return sum;  // Explicit return required
  };
```

 - Single Parameter: Parentheses can be omitted if there's only one parameter.
```
 const square = x => x * x;  // Single parameter, no need for ()
```
 - Multiple Parameters or No Parameters: Parentheses are required.
```
 const add = (a, b) => a + b;  // Multiple parameters
 const greet = () => 'Hello!';  // No parameters
```
 - There are cases where () is used on the right side of the => sign in JavaScript arrow functions:
    - When returning an object literal, you need to wrap the object in parentheses () to distinguish it from a block of code.

    ```const getUser = () => ({ name: 'John', age: 30 });```
    - You can use () to immediately invoke another function within the arrow function.

    ```const callFunction = () => (() => console.log('Hello'))();```
    - Parentheses can be used to group expressions or values.
    
    ```const calculate = (a, b) => ((a + b) * 2);  // Groups the sum of a and b, then multiplies by 2```

