# Kitchen Sink Doc

To be refactored...

----

## [Dependency Inversion Principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle)

> A. High-level modules should not depend on low-level modules. Both should depend on abstractions (e.g., interfaces).
>
> B. Abstractions should not depend on details. Details (concrete implementations) should depend on abstractions."

It is a way for decoupling software modules.

When we design the interaction between a high-level module and a low-level module, the interaction should be abstract, i.e., we should have an interface that describes the interaction. This is good because we can swap the implementation of the modules and things don't break as long as the contract (interface) is kept. This puts an emphasis on the interaction. Developers have to think and focus on defining the interaction as a first class citizen, which by itself helps to avoid coupling.

The idea is to reduce the mutual dependency (coupling) of high-level and low-level modules. So it's easier to reuse both. The "inversion" idea doesn't mean that the low-level modules depend on the high-level ones. But "both layers should depend on abstractions that draw the behaviour needed by higher-level layers".

In terms of packages and architecture:

- The higher/policy layers define the abstractions.
- The higher/policy components and the abstractions for the lower-level layers are in the same package. The lower-level layers inherit or extend those abstractions when are created.

The DIP can also be seen as an example of the adapter pattern. Patterns that help to wire up the low-level modules and concrete implementations when using DIP: Plugin, Service Locator, Dependency Injection

## Implementations:

### 1. Policies and service abstract classes in one package/library

The low-level components need to import the abstract interfaces from the high-level library to be implemented. This *inverts* the dependency between then. The downside is that it makes it difficult to re-utilize, work and implement the low-level modules.

![DIP Implementation 1](../assets/dip_implementation_1.png)
DIP Implementation 1 <sup>1</sup>

### 2. Extract policies, abstractions, and low-level modules in their own packages/libraries

![DIP Implementation 2 - Modified](../assets/dip_implementation_2_modified.png)
DIP Implementation 2 - Modified <sup>2</sup>

A high-level policy has an instance of some code that implements the Policy Services. This code is a mechanim. The mechanism has an instance of some code that implements the Mechanism Services. This code is a utility. The benefit is that we can easily swap code since all the dependencies are based on abstractions.

### References

1. https://en.wikipedia.org/wiki/Dependency_inversion_principle#/media/File:Dependency_inversion.png
2. https://en.wikipedia.org/wiki/Dependency_inversion_principle#/media/File:DIPLayersPattern_v2.png
