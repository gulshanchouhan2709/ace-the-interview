# Block Scope & Shadowing in JS

What is a **Block**?
* Block scope is used to group JS statements together into 1 group. We group them within {...}
    ```js
    {
        var a = 10;
        let b = 20;
        const c = 30;
        // Here let and const are hoisted in Block scope,
        // While, var is hoisted in Global scope.
    }
    ```

* Block Scope and its accessibility example
    ```js
    {
        var a = 10;
        let b = 20;
        const c = 30;
    }
    console.log(a); // 10
    console.log(b); // Uncaught ReferenceError: b is not defined
    ```
    * Reason?
        * In the BLOCK SCOPE; we get b and c inside it initialized as *undefined* as a part of hoisting (in a seperate memory space called **block**)
        * While, a is stored inside a GLOBAL scope. 

        * Thus we say, *let* and *const* are BLOCK SCOPED. They are stored in a separate memory space which is reserved for this block. Also, they can't be accessed outside this block. But var a can be accessed anywhere as it is in global scope. Thus, we can't access them outside the Block.

What is **Shadowing**?

* ```js
    var a = 100;
    {
        var a = 10; // same name as global var
        let b = 20;
        const c = 30;
        console.log(a); // 10
        console.log(b); // 20
        console.log(c); // 30 
    }
    console.log(a); // 10, instead of the 100 we were expecting. So block "a" modified val of global "a" as well. In console, only b and c are in block space. a initially is in global space(a = 100), and when a = 10 line is run, a is not created in block space, but replaces 100 with 10 in global space itself. 
    ```

* So, If one has same named variable outside the block, the variable inside the block *shadows* the outside variable. **This happens only for var**

<hr>