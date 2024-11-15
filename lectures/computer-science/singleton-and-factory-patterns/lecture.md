# Singleton and Factory Patterns

## Singleton Pattern

The Singleton Pattern restricts the instantiation of a class to a single instance. The pattern ensures that only one instance of the class resides in the Java Virtual Machine (JVM), which is used globally.

```java
public class Singleton {
    private static Singleton single_instance = null;

    private Singleton() {
    }

    public static Singleton getInstance() {
        if (single_instance == null)
            single_instance = new Singleton();

        return single_instance;
    }
}
```

In the example above, the constructor is made private to prevent the instantiation of the class from any other class. The `getInstance()` method provides the global point of access to the Singleton object and returns the instance to the caller.

## Factory Pattern

The Factory Pattern is a type of creational pattern that provides one of the best ways to create an object. In Factory pattern, objects are created without exposing the creation logic to the client.

Here is an example of a simple Factory Pattern:

```java
public interface Shape {
    void draw();
}

public class Rectangle implements Shape {
    @Override
    public void draw() {
        System.out.println("Inside Rectangle::draw() method.");
    }
}

public class ShapeFactory {
    public Shape getShape(String shapeType) {
        if (shapeType == null) {
            return null;
        }
        if (shapeType.equalsIgnoreCase("RECTANGLE")) {
            return new Rectangle();
        }
        return null;
    }
}
```

In this example, `ShapeFactory` is a factory class that creates and returns objects of varying classes (i.e., `Rectangle`) based on the input it receives. The client (i.e., the class that calls the `ShapeFactory`) doesn't need to know about the implementing classes, which encapsulates the object creation process.

Both Singleton and Factory Patterns fall under the 'creational pattern' group as they provide one of the best ways to create an object, with Singleton providing a single globally accessible instance and Factory encapsulating the instantiation in a factory class.