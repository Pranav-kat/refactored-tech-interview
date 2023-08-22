---
share: true
---

## Find number of objects created
```java
// Java program Find Out the Number of Objects Created
// of a Class
class Test {

	static int noOfObjects = 0;

	// Instead of performing increment in the constructor
	// instance block is preferred to make this program generic.
	{
		noOfObjects += 1;
	}

	// various types of constructors
	// that can create objects
	public Test()
	{
	}
	public Test(int n)
	{
	}
	public Test(String s)
	{
	}

	public static void main(String args[])
	{
		Test t1 = new Test();
		Test t2 = new Test(5);
		Test t3 = new Test("GFG");

		// We can also write t1.noOfObjects or
		// t2.noOfObjects or t3.noOfObjects
		System.out.println(Test.noOfObjects);
	}
}

```

## Real life applications
1. **Vehicles and Transportation:** The concept of inheritance is seen in vehicle classes. For instance, the hierarchy of vehicles might include a base class "Vehicle," subclasses like "Car," "Motorcycle," and "Truck," which inherit common properties and behaviors from the base class.

2. **Online Shopping:** In e-commerce platforms, items like "Product," "Electronics," "Clothing," etc., can be represented as classes. The concept of encapsulation is applied by hiding the internal details of these classes and exposing only the necessary methods like "getPrice()" and "addToCart()".

3. **Banking System:** In a banking application, customers can be represented as objects of a "Customer" class. Each customer object may have attributes like name, account balance, and methods like "deposit" and "withdraw".

4. **Social Media:** Social media platforms use classes like "User" to represent individuals. These user objects have attributes such as name, age, and methods to interact with the platform, like "postStatus" or "addFriend".

5. **Video Games:** In game development, OOP is used extensively. For instance, a game might have classes for "Player," "Enemy," and "Weapon." These classes encapsulate properties and behaviors specific to their roles.

6. **Cooking:** In cooking, you can think of a "Recipe" class that contains attributes like ingredients and methods like "prepare" and "cook". Inheritance can be applied when you have different types of recipes, like "Dessert" or "Main Course."

7. **Smartphones:** The design of smartphone applications heavily involves OOP concepts. Apps can be modeled as classes, with attributes like "name" and "version," and methods to perform actions like "open" or "update."

8. **Home Automation:** Home automation systems can be modeled using OOP concepts. Each device, like "Light," "Thermostat," or "Smart Plug," can be represented as classes with their unique attributes and methods.

9. **Medical Records:** In healthcare, OOP can be used to model patient records. The "Patient" class can have attributes like name, age, medical history, and methods to schedule appointments or request prescriptions.

10. **Education Systems:** Education platforms can use OOP to represent courses, students, and instructors. The "Course" class can have attributes like name, duration, and methods to enroll students and assign instructors.


## Inheritance Example
```java
class Vehicle {
    private String make;
    private String model;
    private int year;

    public Vehicle(String make, String model, int year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }

    public void displayInfo() {
        System.out.println("Make: " + make);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
    }
}

class Car extends Vehicle {
    private int seatingCapacity;

    public Car(String make, String model, int year, int seatingCapacity) {
        super(make, model, year);
        this.seatingCapacity = seatingCapacity;
    }

    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Seating Capacity: " + seatingCapacity);
    }
}

class Motorcycle extends Vehicle {
    private boolean hasSideCar;

    public Motorcycle(String make, String model, int year, boolean hasSideCar) {
        super(make, model, year);
        this.hasSideCar = hasSideCar;
    }

    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Has Side Car: " + hasSideCar);
    }
}

class Truck extends Vehicle {
    private double loadCapacity;

    public Truck(String make, String model, int year, double loadCapacity) {
        super(make, model, year);
        this.loadCapacity = loadCapacity;
    }

    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Load Capacity: " + loadCapacity);
    }
}

public class TransportationDemo {
    public static void main(String[] args) {
        Car car = new Car("Toyota", "Camry", 2022, 5);
        Motorcycle motorcycle = new Motorcycle("Harley-Davidson", "Street Glide", 2021, false);
        Truck truck = new Truck("Ford", "F-150", 2020, 1500.0);

        System.out.println("Car Information:");
        car.displayInfo();
        System.out.println();

        System.out.println("Motorcycle Information:");
        motorcycle.displayInfo();
        System.out.println();

        System.out.println("Truck Information:");
        truck.displayInfo();
        System.out.println();
    }
}

```

---
**Composition in Java:**

Composition is a design principle in object-oriented programming where a class is composed of one or more objects of other classes. It represents a "has-a" relationship, where a class contains instances of other classes as its members. Composition allows for building complex objects by combining smaller, reusable components.

In composition, the components are often created and managed by the containing class. This provides better encapsulation, as the contained objects are not directly accessible from outside the class, and changes to the implementation of the contained objects do not affect the interface of the containing class.

Here's an example of composition in Java:

```java
class Engine {
    void start() {
        System.out.println("Engine started");
    }
}

class Car {
    private Engine engine;

    public Car() {
        engine = new Engine();
    }

    void startCar() {
        engine.start();
        System.out.println("Car started");
    }
}

public class CompositionExample {
    public static void main(String[] args) {
        Car car = new Car();
        car.startCar();
    }
}
```

In this example, the `Car` class is composed of an `Engine` object. The `Car` class uses composition to encapsulate the functionality of the `Engine` class, allowing the car to start by using its engine.

**Composition vs Inheritance:**

Composition and inheritance are two different ways to achieve code reuse and build relationships between classes:

1. **Composition:**
   - Composition represents a "has-a" relationship.
   - Allows you to create complex objects by combining smaller components.
   - Provides better encapsulation and flexibility, as changes to the components don't affect the containing class's interface.
   - Tends to result in more loosely coupled and maintainable code.
   - Useful when there is no clear hierarchical relationship between classes.

2. **Inheritance:**
   - Inheritance represents an "is-a" relationship.
   - Involves creating a new class (subclass) by inheriting properties and behaviors from an existing class (superclass).
   - Can lead to tight coupling and issues with maintenance, as changes to the superclass can affect all subclasses.
   - Often used when there's a clear hierarchical relationship and shared behaviors between classes.

In general, composition is preferred over inheritance due to its better encapsulation and flexibility. However, the choice between composition and inheritance depends on the specific design requirements and relationships between classes.

I've answered your questions, and you can find the responses in a Markdown file format [here](sandbox:/composition_vs_inheritance.md).