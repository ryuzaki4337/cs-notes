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

- Encapsulation is a fundamental concept in object-oriented programming (OOP) where the internal details (data and logic) of an object are hidden from the outside world. It is the process of bundling the object's data (attributes) and methods (functions) together into a single unit or class. The primary goal is to protect the internal state of an object from unintended modifications and provide controlled access to it.

- Encapsulation enforces data hiding and ensures that attributes (variables) within a class are not directly accessible to other classes or external code. Instead, it provides getter and setter methods to access and modify these private attributes. By making attributes private, encapsulation maintains control over how the data is accessed and modified, preventing unwanted changes or access.

- Importance of Encapsulation:
    - Data Security
    - Flexibility and Maintenance
    - Modular Code
    - Improved Debugging and Testing
    - Reduced Complexity

- Inheritance is a fundamental concept in object-oriented programming (OOP) that allows a class (subclass) to inherit the attributes (fields) and behaviors (methods) of another class (superclass). It is the mechanism that promotes code reuse and establishes a hierarchical relationship between classes.

- Parent Class
    - The parent class (also known as the superclass) is the class that provides common properties (attributes) and behaviors (methods) that are shared by one or more subclasses. It serves as a template or blueprint from which other classes (subclasses) can inherit. For example, School class.
- Subclass (Child Class)
    - A subclass (also known as a child class) is a class that inherits from a parent class. The subclass can reuse, extend, or override the attributes and methods of the parent class to specialize or modify the inherited functionality. For example, Student class.

- In Java, there are three major types of inheritance:
    - Single Inheritance
    - Multilevel Inheritance
    - Hierarchical Inheritance

- Advantages of Using Inheritance
    - Reusability
    - Modularity
    - Extensibility
    - Maintainability

- Multiple inheritance refers to a feature in object-oriented programming where a class can inherit properties and methods from more than one parent class. This allows the child class to combine the functionality of multiple parent classes.

- Java does not allow multiple inheritance using classes to avoid the diamond problem, it allows multiple inheritance through interfaces, as interfaces only declare method signatures (no method bodies initially), thus preventing conflicts.

- Polymorphism is one of the key concepts in object-oriented programming (OOP) and refers to the ability of a single entity (like a method, operator, or object) to behave differently in different contexts.

- There are two main types of polymorphism in Java:
    - Compile-time polymorphism (Method overloading): Multiple methods can have the same name but different parameter lists.
    - Run-time polymorphism (Method overriding): A method in the child class can have the same name and parameters as in the parent class, but the child class provides its own implementation.

- Note that the return type cannot be a differentiator for Method Overloading.

- A static method cannot be overriden.

- Abstraction is one of the fundamental concepts of Object-Oriented Programming (OOP). It is the process of hiding the implementation details and showing only the necessary features or interface to the user.

- Abstraction is achieved through abstract classes and interfaces in languages like Java.

- Key Features of Abstraction:
    - Hiding Implementation Details
    - Abstract Methods
    - Concrete Methods

- Benefits of Abstraction in Programming
    - Simplify the system
    - Improve maintainability
    - Increase reusability
    - Provide security

- An abstract class can inherit from another abstract class just like a regular class would. The subclass (child abstract class) will inherit the abstract methods and behaviors of the parent class, but it is not required to implement the abstract methods from the parent class unless it is a concrete class (i.e., a class that is not abstract). If the subclass is also abstract, it can either:
    - Implement the abstract methods from the parent class, or
    - Leave them unimplemented (in which case, the subclass must also be declared as abstract).

- An abstract class is designed to be inherited by other classes, and it is not meant to be instantiated on its own. However, an abstract class can have a constructor, which can be invoked by a subclass when an instance of the subclass is created. This allows the abstract class to initialize its fields before the subclass adds its own specific behaviors.

- Abstract Class Constructor: An abstract class can have constructors, but you cannot create an instance of the abstract class directly. The constructor is only called when a subclass object is created.

- Subclass Constructor: When a subclass is instantiated, its constructor can call the constructor of the abstract class using the super() keyword.

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

- An interface in Java is a blueprint of a class that defines a contract for behavior but does not provide an implementation. It contains a set of abstract methods (methods without a body) that a class must implement if it chooses to "sign the contract" by implementing the interface.

- An interface cannot have instance variables. All fields in an interface are implicitly public, static, and final. This means they act as constants and cannot be changed. Attempting to declare a non-static or non-final field will result in a compilation error.

- Interfaces cannot have constructors. 

- A class in Java can implement multiple interfaces.

- Key Features of Interfaces:
    - Multiple Inheritance
    - Contracts
    - Loosely Coupled Systems

- Interfaces in Java can extend other interfaces, allowing for inheritance. When an interface inherits another, it can add new methods to the contract defined by the parent interface.

- Interfaces:
    - Pure abstraction: An interface only defines what methods should be present, the actual implementation is provided by the class that implement the interface.
    - No instantiation: Similar to abstract classes, they serve only as blueprint.
    - Multiple implementation: A class can implement multiple interfaces, allowing for more flexibility compared to single inheritance in classes.
    - Loose coupling: Interfaces help to reduce the dependencies between parts of the code, making the system more modular and easier to maintain.

- The static keyword is used to indicate that a member belongs to the class rather than to any specific instance of the class. It can be applied to variables, methods, blocks, and nested classes. Members marked as static are shared across all instances of the class, meaning they are loaded only once in memory during the class's lifecycle.

- Static methods cannot directly access or invoke non-static methods or variables because static methods do not depend on a class instance. However, non-static members can be accessed indirectly by creating an instance of the class.

- Advantages of Static Members in Java:
    - Memory Efficiency: Static variables are loaded into memory only once, reducing memory usage.
    - Utility Functions: Static methods are ideal for utility or helper methods that do not require object-specific data (e.g., Math.sqrt()).
    - Initialization: Static blocks allow for the initialization of static variables, ensuring that common resources are ready for use.

- Inner classes are classes that are defined within another class.

- Relationships between classes can be categorized into three major types:
    - Association: A general relationship where one class interacts with another.
    - Aggregation: A specialized form of association that represents a "has-a" relationship with a weaker bond.
    - Composition: A more restrictive form of aggregation where the lifecycle of the related objects is tightly coupled.

- In real-world systems, a class can participate in multiple types of relationships simultaneously.

- Cloning in Java can be categorized into two types:
    - Shallow Cloning: Copies primitive fields and references for objects. The cloned object shares the same reference for nested objects.
    - Deep Cloning: Creates a completely independent copy of the original object, including copies of all nested objects.

- An object in Java typically follows this lifecycle: Creation → Usage → Garbage Collection → Destruction
    - Creation: Allocated memory on the heap using new.
    - Usage: Methods and fields of the object are used.
    - Garbage Collection: When no references point to the object, it becomes eligible for GC.
    - Destruction: JVM garbage collector destroys and reclaims the memory.