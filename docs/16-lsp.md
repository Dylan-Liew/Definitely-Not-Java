# Liskov Substitution Principle Summary

## LSP Definition
- Subtype must be completely substitutable for its supertype
- Subtype must preserve behavior expected of supertype
- **Formal Definition**: Let φ(x) be a property provable about objects x of type T. Then φ(y) should be true for objects y of type S where S <: T

## LSP Violations Example
```java
class Course {
    char getGrade(int marks) {
        // Returns 'A', 'B', 'C', or 'F'
        return grade;
    }

    void displayGrade(Course c, double marks) {
      char grade = c.marksToGrade(marks);
      if (grade == 'A')) {
        System.out.println("well done");
      else if (grade == 'B') {
        System.out.println("good");
      else if (grade == 'C') {
        System.out.println("ok");
      } else {
        System.out.println("retake again");
      }
    }
}

class CSCUCourse extends Course {
    @Override
    char getGrade(int marks) {
        // LSP Violation: Returns 'S' or 'U'
        // Breaks code expecting A,B,C,F
        return grade;
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
        // Contract: Accept all times between opening and closing
        return time >= OPENING_HOUR && time <= CLOSING_HOUR;
    }
}

class LunchRestaurant extends Restaurant {
    @Override
    boolean canMakeReservation(int time) {
        // LSP Violation: Rejects valid times
        // Breaks contract of accepting all times within range
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
