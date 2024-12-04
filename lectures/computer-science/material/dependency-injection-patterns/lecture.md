# Dependency Injection Patterns

Dependency injection is a technique whereby one object supplies the dependencies of another object. Here are some common patterns:

## Constructor Injection

Constructor injection is a form of DI where dependencies are provided through a class constructor. It's the most common DI pattern, providing a clear contract for required dependencies. Immutable objects can also be created with this pattern.

```java
public class Client {
    private final Service service;

    public Client(Service service) {
        this.service = service;
    }
}
```

In this example, `Client` class depends on `Service` class. The `Service` is injected through the constructor.

## Setter Injection

Setter injection is a form of DI where dependencies are provided through JavaBean properties (ex. a setter method). Allows optional dependencies.

```java
public class Client {
    private Service service;

    public void setService(Service service) {
        this.service = service;
    }
}
```

In this example, `Client` class depends on `Service` class. The `Service` is injected through a setter method.

## Interface Injection

Interface injection is a form of DI where the dependency provides an injector method that will inject the dependency.

```java
public interface ServiceSetter {
    public void setService(Service service);
}

public class Client implements ServiceSetter {
    private Service service;

    public void setService(Service service) {
        this.service = service;
    }
}
```

Here, `Client` implements the `ServiceSetter` interface and the `Service` is injected through the `setService` method.

These patterns provide a way to compose objects in a flexible and extensible manner. They make your code more testable, modular, and maintainable.
