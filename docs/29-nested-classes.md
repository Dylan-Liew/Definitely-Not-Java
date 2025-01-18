# Nested Classes Summary

## Types of Nested Classes
1. Static Nested Classes
2. Inner Classes (Non-static)
3. Local Classes
4. Anonymous Classes

## Static Nested Classes
- Declared with static modifier
- Cannot access instance members of outer class
- Example:
  ```java
  class Outer {
    private static int x;
    
    static class StaticNested {
      void method() {
        x = 1;  // can access static members
      }
    }
  }
  ```

## Inner Classes
- Has access to all outer class members
- Requires instance of outer class
- Example:
  ```java
  class Outer {
    private int x;
    
    class Inner {
      void method() {
        x = 1;  // can access instance members
        Outer.this.x = 2;  // explicit outer reference
      }
    }
  }
  ```

## Local Classes
- Defined inside methods
- Can access local variables (must be final/effectively final)
- Example:
  ```java
  void method() {
    final int x = 1;
    class Local {
      void innerMethod() {
        System.out.println(x);  // can access final local vars
      }
    }
  }
  ```

## Anonymous Classes
- Class definition and instantiation combined
- Often used for interfaces/abstract classes
- Example:
  ```java
  Runnable r = new Runnable() {
    @Override
    public void run() {
      System.out.println("Running");
    }
  };
  ```

## Variable Capture
- Local and anonymous classes can capture variables
- Variables must be final or effectively final
- Example:
  ```java
  void method() {
    final int x = 1;
    Runnable r = new Runnable() {
      @Override
      public void run() {
        System.out.println(x);  // captures x
      }
    };
  }
  ```

## Best Practices
- Use static nested classes when possible
- Keep inner classes small and focused
- Consider lambda expressions instead of anonymous classes
- Be careful with variable capture
- Document nested class relationships
- Use nested classes for encapsulation
