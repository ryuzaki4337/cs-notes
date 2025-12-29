- OOPS(Object-Oriented Programming System) is a programming paradigm based on concepts of classes and objects, which can contain data and code to manipulate that data.

- Class: In Java, a clas serves as a blueprint or a template for creating objects.

- Object: An object is an instance of a class.

- Access Specifier: Determine the visibility and accessibility of classes, methods and variables.

- Public: Accessible from anywhere in the code.

- Private: Restricts its access to within the class it is declared in.

- Protected: A protected entity is accessible within its own package and by sub-classes.

- If no specifier is used, Java assigns a default access level, known as package-private, meaning the class or method is accessible only within its own package.

- Static: Keyword allows JVM to call any variable / method without creating an instance of the class.

- Arguments are the values or variables passed to a function or method when it is called.

- Constructor: Special type of method used to initialize objects.
    - Default constructor
    - Parameterized constructor

- In Java, a class can have multiple constructorss, a concept known as constructor overloading.

- Encapsulation: Practove of bundling data (variables) and methods that operate on the data into a single unit, know as the class, restricting direct access to the date from outside the class.
    - Data hiding: Encapsulation hides the internal details of how an object works. THe object's data is kept private and can be accessed or modified through getters and setters.
    - Controlled Access: Through encapsulation, only specific methods are provided to access or modify the data, ensuring more controlled and secure interactions with the object's data.

- Inheritance: Allows a class to inherit properties and behaviors (fields and methods) from another class. Helps in re8using existing code and creating a hierarchial relationships between classes.
    - Parent (Super class) and Child (Sub class): In inheritance, the class that is inherited from is Parent class and the class that inherits is called Child class.
    - Reuse of code: Child class automatically gets the methods of parent class.
    - Extending functionality: The child clas can add new features or override existing ones to modify the behavior inherited from parent class.

- Polymorphism: Allows objects to be treated as instances of their parent class on interface, while having the ability to take on different forms or behaviors. It enables the same method to perform different actions depending on the object calling it.
    - Compile-time polymorphism (Method overloading): Multiple methods can have the same name but different parameter lists.
    - Run-time polymorphism (Method overriding): A method in the child class can have the same name and parameters as in the parent class, but the child class provides its own implementation.

- Abstraction: Focuesses on hiding complex implementation details and exposing only the essential featutres of object or methods.
    - Hides complexity: Abstraction allows a user to interact with an object or method without neding to understand the underlying details of how it works.
    - Simplies interaction: Only the important aspects are exposed, making it easier to use the object / method.
    - In Java, abstraction can be achieved through 
        * Abstract classes
        * Interfaces

- Abstract classes:
    - Cannot be instantiated: An abstract class cannot be used to create objects directly. It must be inherited by a subclass, and only the subclass can be instantiated.
    - Abstract Methods: These are methods without implementation in the abstraction class, and the subclass are requried to provie their own implementation.
    - Can have regular methods: Along with abstract methods, an abstract class can also have fully defined methods.

- Interfaces:
    - Pure abstraction: An interface only defines what methods should be present, the actual implementation is provided by the class that implement the interface.
    - No instantiation: Similar to abstract classes, they serve only as blueprint.
    - Multiple implementation: A class can implement multiple interfaces, allowing for more flexibility compared to single inheritance in classes.
    - Loose coupling: Interfaces help to reduce the dependencies between parts of the code, making the system more modular and easier to maintain.