- Single Responsibility Principle (SRP): A class should have only one reason to change. In other words, a class should only have one job, one responsibility, and one purpose.

- Advantages of SRP
    - Improved Maintainability
    - Enhanced Readability
    - Better Reusability
    - Facilitates Testing
    - Lower Risk in Changes

- Open Closed Principle (OCP): As per OCP, Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification. This means that the behavior of a module can be extended without modifying its source code. The goal is to reduce the risk of breaking existing functionality when requirements change.

- Liskov Substitution Principle (LSP): If S is a subtype of T, then objects of type T may be replaced with objects of type S without altering the correctness of the program.
This means that any subclass should be substitutable for its parent class without breaking the functionality.

- Key Principles of LSP:
    - Subclasses should honor the contract (expectations) of the parent class.
    - Avoid overriding methods in a way that changes behavior drastically.
    - Prefer composition over inheritance when possible.
    - Think in terms of interfaces and behavioral compatibility.
    - Subclass should only extend, not restrict behavior.

- Interface Segregation Principle (ISP): Don't force a class to depend on methods it does not use.

- Benefits of using ISP:
    - Cleaner Codebase: Classes are not bloated with irrelevant methods.
    - Better Flexibility: Easier to change one part without affecting others.
    - High Maintainability: Smaller interfaces are easier to understand and test.
    - Fewer Bugs: Less chance of someone accidentally using or overriding a method they don't need.
    - Scalability: As your app grows, adding new roles (like delivery partners in Uber Eats) becomes easier.

- High-Level Modules: The parts of your code that contain the core logic — the brains of your application. They make big decisions and coordinate how different features work together. Example: CEO (makes decisions, plans strategies).

- Low-Level Modules: The ones that handle the details — like talking to a database, making API calls, reading files, or providing data. They support the high-level logic by doing the grunt work. Example: Employees (do the actual implementation, logistics, and execution).

- Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

- Benefits of using DIP:
    - Flexibility: Easily swap out implementations without modifying high-level code.
    - Testability: You can mock or stub the abstractions during testing.
    - Reusability: Code becomes reusable since it's not tightly bound to one specific implementation.
    - Maintainability: Makes it easier to change one part of the system without affecting others.
    - Scalability: You can scale or upgrade parts of your codebase without a massive rewrite.