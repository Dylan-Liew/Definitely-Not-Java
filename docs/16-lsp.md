# Liskov Substitution Principle Summary

## LSP Definition
- If S is a subtype of T, then objects of type T may be replaced with objects of type S
- Properties true for supertype must be true for subtype
- Subtype must preserve behavior expected of supertype
- Formal definition: Let φ(x) be a property of x of type T. Then φ(y) should be true for objects y of type S where S <: T

## LSP Violations Example
```java
class Course {
  char getGrade(int marks) {
    return 'A', 'B', 'C', or 'F';
  }
}

class CSCUCourse extends Course {
  @Override
  char getGrade(int marks) {
    return 'S' or 'U';  // Violates LSP
  }
}
```

## Testing Perspective
- Subclass should pass all superclass tests
- Example:
```java
class Restaurant {
  public static final int OPENING_HOUR = 1200;
  public static final int CLOSING_HOUR = 2200;
  
  boolean canMakeReservation(int time) {
    return time >= OPENING_HOUR && time <= CLOSING_HOUR;
  }
}

class LunchRestaurant extends Restaurant {
  @Override
  boolean canMakeReservation(int time) {
    // Violates LSP by rejecting valid times
    return time >= 1400 && time <= CLOSING_HOUR;
  }
}
```

## Preventing Inheritance
- Use `final` keyword to prevent inheritance
- Example:
```java
final class String {  // Cannot be inherited
  // implementation
}
```

## Preventing Method Overriding
- Use `final` keyword on methods
- Prevents subclasses from changing behavior
- Example:
```java
class Circle {
  final double getArea() {  // Cannot be overridden
    return Math.PI * r * r;
  }
}
```

## Best Practices
- Design inheritance hierarchies carefully
- Document expected behavior and constraints
- Use `final` when inheritance not intended
- Test subclasses against superclass contracts
- Consider composition over inheritance
- Make classes immutable when possible
- Write clear specifications for methods
