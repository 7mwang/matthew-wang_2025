---
layout: post
title: AP Exam Study Cheat Sheet/Notes
permalink: /AP-Study
comments: True
---
# CB Topics Cheat Sheet

## Key Sites
[Geeks for Geeks](https://www.geeksforgeeks.org/java/)

[W3 Schools](https://www.w3schools.com/java/)

# Topic Summary
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

# MCQ

![Image](https://github.com/user-attachments/assets/cc276163-0bc3-4427-ae16-4317c21ef6a1)

![Image](https://github.com/user-attachments/assets/414773e2-ceb6-4c12-acbc-3508aa56acc2)

![Image](https://github.com/user-attachments/assets/e37a3ea3-26f2-4895-864a-5a9ec8b6c052)

![Image](https://github.com/user-attachments/assets/add2d5b8-fe92-4c91-8c96-df7f6081ffe0)

![Image](https://github.com/user-attachments/assets/50214dbd-88a4-4d91-a27d-edf16eeb1e50)

# FRQ

![Image](https://github.com/user-attachments/assets/88f062ba-c37c-4274-ae70-501dc553d7ec)

## 2014: Problem 1 Work Revised
(Coded in REPL, includes test case)
```
public class Main {
  public static void main(String[] args) {
    recombine("john", "mort");
    String[] words = {"apple", "pear", "this", "cat", "doge", "fish", "blat", "pent"};
    mixedWords(words);
  }
  public static String recombine(String word1, String word2) {
    String finalString = "";
    String[] words = {word1, word2};
    for(int i = 0; i < words.length; i++) {
      if(i == 1) {
        for(int j = words[i].length()/2; j < words[i].length(); j++) {
          finalString += words[i].charAt(j);
        }
      }
      else {
        for(int j = 0; j < words[i].length()/2; j++) {
          finalString = finalString + words[i].charAt(j);
        }
      }
    }
    System.out.println(finalString);
    return finalString;
  }
  public static String[] mixedWords(String[] words) {
    String tempW = "";
    for(int i = 0; i < words.length; i+=2) { 
      tempW = recombine(words[i], words[i+1]);
      words[i+1] = recombine(words[i+1], words[i]);
      words[i] = tempW;
    }
    return words;
  }
}
```
### Output
```
jort
apar
peple
that
cis
dosh
fige
blnt
peat
```