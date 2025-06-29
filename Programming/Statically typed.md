- Meaning the type of every expression in a program is known at compile time, and the compiler can validate that the methods and fields you're trying to access exist on the objects you are using.

**Benefits:**
- Performance - Calling methods is faster because there's no need to figure out at runtime which method needs to be called
- Reliability - Checks are done at compile time leading to less crashes at runtime
- Maintainability - Working with unfamiliar code is easier because you can see what kind of objects the code is working with
- Tool support - Static typing enables reliable refactorings, precise code completion, and other IDE features