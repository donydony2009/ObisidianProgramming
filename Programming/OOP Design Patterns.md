
## Creational
### Factory Method
Usually used  when you need to do additional things on object creation. Things like caching, memorizing its reference, registering it to things such as serialization.

Alternatively you might use it if you need to do some data gathering for this creation.

### Abstract factory
It's a factory that creates abstract objects based on parameters without having to know the underlying object

### Builder
This facilitates object creation by using a Builder. This is useful when you have a bunch of parameters to configure for the object.

Examples: creating a query, creating http request, creating a prom metric

### Prototype

an object with the method `clone`? ?

### Singleton
this has 2 components:
1. Usually globally available
2. One and only one object can exist

## Structural
### Adapter
Facilitates the communication between 2 objects with incompatible interfaces

### Bridge
Is basically just an api. more like API + abstractization for the actor trying to interact

![[Pasted image 20240804134948.png]]
### Composite
Basically inheritance vs composition. Allows you to compose objects out of components. It has advantage of being able to extend in multiple directions

### Decorator
A wrapper around a function or object. Allowing you to do something before or after the execution, or adding some stuff.

You could for example use it for dependency injection

### Facade
A simplified interface for a complicated library/framework or any complex system

### Proxy
Basically a wrapper around an object allowing you to do something when executing anything in the object

## Behavioral

### Chain of responsibilty
A chain of handlers which for which if one fails the chain fails if it's success the next handler is executed
Can be used for telemetry -> auth -> validation -> req processing

### Command
A class containing everything needed to execute an action. Useful to encapsulate an action so you can refer to it from multiple places

### Iterator
A way to traverse a collection of stuff

### Mediator
A central class that mediates communication between various objects

### Memento
A way to save the current state such that we might come back to it later

### Observer
A way to notify parties if something changes. It is esentially a function is called when something needs to be observed

### State
Esentially refers to state machine. Each state is a class which does stuff on state change on state execute bla bla

### Strategy
A swappable function that serves as a strategy to execute. For example retry strategy could be exponential, immediate, liniar

### Template method
A class that serves as a skeleton for doing a process. It would have something like doX, doY, checkZ and all these methods can be overriden through inheritance

### Visitor
A way to go through a collection by executing a function for each object. Can be used as a for each. An example would be if you wanted to go through a graph.
