- Procedural programming is a software development method that is executed step by step in a certain manner. Data is exposed and code cannot be reused much. Ex. C, Pascal.

- OOPS(Object-Oriented Programming System) is a programming paradigm based on concepts of classes and objects, which can contain data and code to manipulate that data.

- Uses of OOPs: Modular, Reusable, Scalable, Security. (Hence better for large scale apps)

- Class: In Java, a clas serves as a blueprint or a template for creating objects.

- Object: An object is an instance of a class. (Bundles of variables and methods.)

- Attributes (also called properties or fields) are the data or characteristics of an object. For example, In the Employee class, there are two attributes: employeeName and salary.

- Behaviors (also called methods or functions) are the actions or operations that an object can perform. For example, In the Employee class, there are three behaviours/methods: setName(), setSalary() and getSalary().

- In Java, objects are deleted automatically by the Garbage Collector (GC). Java handles memory management and deallocates objects that are no longer in use or referenced, which helps avoid memory leaks. An object becomes eligible for deletion when there are no active variable or reference pointing to it. The garbage collector periodically scans the heap memory to identify and collect objects that are no longer being used.

- Stack Memory:
    - The stack is where primitive variables (such as int, double, boolean) and references to objects (like obj1) are stored.
    - obj1 will hold the reference (memory address) of the object created by new Employee().
    - When the main method finishes executing, the stack memory associated with obj1 will be cleared, but the object in the heap will remain as long as there are references pointing to it.

- Heap Memory
    - The heap is where objects (instances of classes) are stored. The object created by new Employee() is allocated memory in the heap.
    - The Employee object will have its attributes (e.g., salary, employeeName) stored here.
    - This memory will remain allocated as long as there are references pointing to it. Once there are no more references to the object (i.e., the reference in the stack becomes null or goes out of scope), the object can be garbage collected.

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
    - Copy constructor

- In most of the OOP languages(C++, Java), the compiler stops generating the default constructor as soon as we define one ourselves.

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