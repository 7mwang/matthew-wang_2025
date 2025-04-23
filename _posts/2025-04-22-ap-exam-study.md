---
layout: post
title: AP Exam Study Cheat Sheet/Notes
permalink: /AP-Study
comments: True
---
# CB Topics Cheat Sheet

## Primitive Types
- Java has 8 primitive types: `int`, `double`, `boolean`, `char`, `byte`, `short`, `long`, `float`.
- Variables store simple values, e.g., `int x = 5;` or `double price = 3.99;`.
- `int` for whole numbers, `double` for decimals, `boolean` for `true/false`.

## Objects
- Classes define object types, and objects are instances of those classes.
- Use `new` keyword to create objects: `String s = new String("hello");`.
- Call methods with dot notation: `s.length()` or `Math.abs(-4)`.

## Boolean Expressions and if Statements
- Booleans: `true`, `false`; operators: `&&`, `||`, `!`.
- Conditional statements:
  ```java
  if (x > 5) {
      // do something
  } else {
      // do something else
  }
  ```
- Use `equals()` to compare strings: `str1.equals(str2)`.

## Iteration
- `for`, `while`, and `do-while` loops repeat blocks of code.
- Common use: traversing arrays or ArrayLists.
  ```java
  for (int i = 0; i < arr.length; i++) {
      // loop body
  }
  ```

## Writing Classes
- A class includes fields, constructors, and methods.
  ```java
  public class Dog {
      private String name;
      public Dog(String n) { name = n; }
      public String getName() { return name; }
  }
  ```

## Array
- Fixed-size containers: `int[] nums = new int[5];`.
- Use `nums.length` and index access: `nums[0] = 1;`.

## ArrayList
- Resizable array: 
  ```java
  ArrayList<String> list = new ArrayList<>();
  list.add("hello");
  list.get(0);
  ```
- Requires `import java.util.ArrayList;`.

## 2D Array
- Arrays of arrays:
  ```java
  int[][] grid = new int[3][4];
  grid[0][1] = 5;
  ```
- Access with `grid[row][col]`; use nested loops to iterate.

## Inheritance
- A subclass inherits from a superclass using `extends`.
  ```java
  public class Dog extends Animal {
      // subclass code
  }
  ```
- Use `super()` to call superclass constructors or methods.

## Recursion
- A method that calls itself.
- Must include a base case and a recursive case.
  ```java
  public int factorial(int n) {
      if (n == 0) return 1;
      return n * factorial(n - 1);
  }
  ```

# MCQ Reflections: 2020 Practice Exam 1 MCQ
