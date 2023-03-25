## IoC and DI

### Inversion Of Control (IoC)

According to the paper written by Martin Fowler , inversion of control is the principle where the control flow of a program is inverted: instead of the programmer controlling the flow of a program, the external sources (framework, services, other components) take control of it. It's like we plug something into something else.

In this we transfers the control of objects or portions of a program to a container or framework. 

In contrast with traditional programming, in which our custom code makes calls to a library, IoC enables a framework to take control of the flow of a program and make calls to our custom code.

The advantages of this architecture are:

-   decoupling the execution of a task from its implementation
-   making it easier to switch between different implementations
-   greater modularity of a program
-   greater ease in testing a program by isolating a component or mocking its dependencies, and allowing components to communicate through contracts

We can achieve Inversion of Control through various mechanisms such as: Strategy design pattern, Service Locator pattern, Factory pattern, and Dependency Injection (DI).

### Dependency Injection (DI)

Dependency Injection is a design pattern which implements IOC principle. DI provides objects that an object needs. Let’s say, class X is dependent on Y. So rather than creating object of Y within the class “X”, we can inject the dependencies via a constructor or setter injection.

Connecting objects with other objects, or “injecting” objects into other objects, is done by an assembler rather than by the objects themselves. It's a more specific version of IoC pattern, where implementations are passed into an object through constructors/setters/service lookups, which the object will "depend" on in order to behave correctly.


The advantages of this architecture are:

-   Loose coupling between the components
-   Minimising the amount of code in your application
-   Makes unit testing easy with different mocks
-   Increased system maintainability and module reusability
-   Allows concurrent or independent development
-   Replacing the modules as no side effects
-   
-   making it easier to switch between different implementations
-   greater modularity of a program
-   greater ease in testing a program by isolating a component or mocking its dependencies, and allowing components to communicate through contracts