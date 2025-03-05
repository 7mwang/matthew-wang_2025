---
layout: post
title: MCQ Corrections 2015
permalink: /mcq/2015
comments: True
---

# Key Problems:

## Time Crunch
- I noticed myself being rushed, because I tried my best to finish it in the classtime we were given, and I started late into class. This kind of simulates the AP exam, where we will be limited on time, and especially near the end, I couldn't spend as much time reading the questions, leading to multiple answers that I should have gotten right being incorrect.


# Q27: Sorting a 1D int array

{1, 3, 2, 5, 4, 6}

Answer E
Incorrect. This is the result of one pass through the outer loop.

{1, 2, 3, 5, 4, 6}

Answer B
Correct. The selection sort algorithm shown looks for the smallest value in the elements ranging from index j to the end and swaps the smallest value with the value at position j. In the first pass, 1 is the smallest element from position j = 0 to the end of the array, so it is swapped with 6, resulting in {1, 3, 2, 5, 4, 6}. In the second pass, 2 is the smallest element from position j = 1 to the end of the array, so it is swapped with 3, resulting in {1, 2, 3, 5, 4, 6}. In the third pass, 3 is the smallest element from position j = 2 to the end of the array, it is swapped with itself, resulting in {1, 2, 3, 5, 4, 6}.

# Q31: X and O board

Board with X pattern

Answer C
Incorrect. This image could be accomplished by iterating board and setting all locations where row == col to “X” and all locations where row + column == board.length-1 to “X”.

Board with two diagonal lines in upper left
Answer E
Correct. The first set of nested for loops sets each element in board to “O”. The next for loop starts val at 0 and increments by 1 until val is 4, when val is 5 the loop terminates. When val is even, board is not updated, so nothing happens when val is 0. When val is 1, row is assigned 1 and col is assigned 0. The boolean condition in the while loop is true, so board[1][0] is assigned “X”. Then col is incremented to 1 and row is decremented to 0 and board[0][1] is assigned “X”. Then col is incremented to 2 and row is decremented to -1 and the while loop terminates. When val is 2, nothing changes about board. When val is 3, row is assigned 3 and col is assigned 0. The boolean condition in the while loop is true, so board[3][0] is assigned “X”. Then col is incremented to 1 and row is decremented to 2 and board[2][1] is assigned “X”. Then col is incremented to 2 and row is decremented to 1 and board[1][2] is assigned “X”. Then col is incremented to 3 and row is decremented to 0 and board[0][3] is assigned “X”. Finally, col is incremented to 4 and row is decremented to -1 and the while loop terminates. When val is 4, nothing changes about board.

# Q32 StudentInfo class and averageInMajor method

if (theMajor.equals(k.major()))

Answer C
Incorrect. Instance variable major is private to StudentInfo and can only be accessed by calling the accessor method getMajor.


if (theMajor.equals(k.getMajor()))

Answer B
Correct. To calculate the average age in a given major, you have to find all the students in the given major, add up their ages, and divide by the total number of students in the major. Since theMajor is a String, the if statement needs to use .equals to compare theMajor with the major of k, found by calling the getMajor() method on k. If this boolean expression is true, we need to add the age of k, found by calling the getAge() method on k to sum and increase count by 1.

# Q35 Iterative binarySearch of 1D int array

3

Answer B
Incorrect. This would be returned if the algorithm was counting the number of times 8 occurs in values rather than finding the index where 8 occurs in values.

5

Answer C
Correct. In the first iteration of the binary search, it will check the value at index (0 + 7) / 2 which is index 3. Since 8 is greater than data[3], start is assigned mid + 1 which is 4 and the process will repeat. In the second iteration of the while loop, it will check the value at index (4 + 7) / 2 which is index 5. Since data[5] is 8, 5 is returned.

# Q39 Consider the following code segment.

Alex Alex Alex

Alex Bob Carl

Answer B
Incorrect. In this case the lines of output are reversed.

Alex Bob Carl

Alex Alex Alex

Answer C
Correct. The first for loop uses the set method to change the value of each element in students to “Alex”. When the set method is called, it returns the value that was originally at this index. So, the first loop will print Alex Bob Carl. At this point all elements have been set to “Alex”. The second for loop uses an enhanced for loop to access every element and will print Alex Alex Alex.