### Java Developer Realtime Interview Questions & Answers

> Click :star: if you like the project. Pull Request is highly appreciated. Follow me [@AltafJava](https://twitter.com/altafjava) for technical updates.

## Table of Contents

| No. | Questions                                                                                                                                                          |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|     | **Core**                                                                                                                                                           |
| 1   | [Write an implementation for this funtional interface?](#Write-an-implementation-for-this-funtional-interface)                                                     |
| 2   | [Difference between map and flatmap in Java 8?](#Difference-between-map-and-flatmap-in-Java-8)                                                                     |
| 3   | [Find the total marks of all students using Java 8 stream.](#Find-the-total-marks-of-all-students-using-Java-8-stream)                                             |
| 4   | [Sort the students in descending order based on their marks using Java 8 stream.](#Sort-the-students-in-descending-order-based-on-their-marks-using-Java-8-stream) |
| 5   | [What will be the output of the following code?](#What-will-be-the-output-of-the-following-code-5)                                                                 |
| 6   | [What will be the output of the following code?](#What-will-be-the-output-of-the-following-code-6)                                                                 |
|     | **Logical**                                                                                                                                                        |
| 1   | [Reverse this array without new array.](#Reverse-this-array-without-new-array)                                                                                     |

## Core

1. ### Write an implementation for this funtional interface?

   ```java
   public interface functionalInterface {
      void read(int a);
   }
   ```

   ```java
   public class FunctionalInterfaceImpl {
       public static void main(String[] args) {
           functionalInterface f = (a) -> System.out.println("Value is: " + a);
           f.read(10);
       }
   }
   ```

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

2. ### Difference between map and flatmap in Java 8.

   In Java 8, `map` and `flatMap` are both methods in the Stream interface used for transforming elements. However, they serve different purposes and operate in distinct ways.

   - **map**: The `map` method transforms each element of a stream into another object using the provided function. It applies the function to each element of the stream independently and returns a new stream containing the transformed elements. The function passed to the `map()` operation returns a single value for each input, resulting in a one-to-one mapping. Essentially, `map()` is used solely for transformation, producing a stream of values.

     ```java
     List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);
     List<Integer> mapResult = list.stream().map(x -> x * 2).collect(Collectors.toList());
     System.out.println(mapResult); // prints [2, 4, 6, 8, 10]
     ```

   - **flatMap**: The `flatMap` method transforms each element of a stream into a stream of objects and then combines all those streams into a single stream. It is particularly useful when we want to flatten a stream of collections or arrays into a single stream of elements. The function you pass to the `flatMap()` operation can return an arbitrary number of values for each input, facilitating a one-to-many mapping. This method performs both transformation and flattening, producing a stream of stream values, and is used for both transformation and mapping.

     ```java
     List<List<Integer>> list = Arrays.asList(Arrays.asList(1, 2), Arrays.asList(3, 4), Arrays.asList(5, 6));
     List<Integer> flatMapResult = list.stream().flatMap(Collection::stream).collect(Collectors.toList());
     System.out.println(flatMapResult); // prints [1, 2, 3, 4, 5, 6]
     ```

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

3. ### Find the total marks of all students using Java 8 stream.

   ```java
    List<Student> student = Arrays.asList(
            new Student(1, "Alice", 85),
            new Student(2, "Bob", 92),
            new Student(3, "Charlie", 78),
            new Student(4, "David", 95)
    );
   ```

   ```java
    int totalMarks = student.stream().mapToInt(Student::getMarks).sum();
   ```

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

4. ### Sort the students in descending order based on their marks using Java 8 stream.

   ```java
   List<Student> student = Arrays.asList(
           new Student(1, "Alice", 85),
           new Student(2, "Bob", 92),
           new Student(3, "Charlie", 78),
           new Student(4, "David", 95)
   );
   ```

   ```java
    List<Student> sortedStudents = student.stream()
            .sorted(Comparator.comparing(Student::getMarks).reversed())
            .collect(Collectors.toList());
   ```

   ```java
   List<Student> sortedStudents = students.stream()
    .sorted((emp1, emp2) -> emp2.getMarks().compareTo(emp1.getMarks()))
    .collect(Collectors.toList());
   ```

   <div align="right">
       <b><a href="#core">⬆ Back to Top</a></b>
   </div>

5. ### What will be the output of the following code 5?

   ```java
   Employee emp1 = new Employee(1, "Alice", 85)
   Employee emp2 = new Employee(1, "Alice", 85)
   boolean b1 = emp1 == emp2
   boolean b2 = emp1.equals(emp2)
   ```

   **Answer:** `b1` will be `false` because `==` checks for reference equality, and `emp1` and `emp2` are two distinct objects.
   `b2` will be `false` because the default `equals()` method in Object also checks for reference equality. Unless equals() is overridden in the Employee class to compare the attributes, it behaves the same as `==`.

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

6. ### What will be the output of the following code 6?

   ```java
   static int except()
   {
       try
       {
           int a = 10;
           return 1;
       }
       catch(Exception e)
       {
           return 2;
       }
       finally {
           return 3;
       }
   }
   ```

   **Answer:** The `finally` block will always execute, regardless of whether an exception is thrown or not. In this case, the `finally` block returns `3`, which overrides the return value of `1` in the `try` block. So, the output will be `3`.

   - In this case, the try block executes and returns 1.
   - Before the method actually returns 1, the finally block is executed.
   - The finally block contains a return statement that returns 3, which overrides the previous return value.

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

## Logical

1. ### Reverse this array without new array.

   Input: `{ 2,9,4,7,1,6 }`

   ```java
   public class ReverseArray {
       public static void main(String[] args) {
           int[] arr = { 2, 9, 4, 7, 1, 6 };
           System.out.println("Before: " + Arrays.toString(arr));
           for (int i = 0; i < arr.length / 2; i++) {
               int temp = arr[i];
               arr[i] = arr[arr.length - 1 - i];
               arr[arr.length - 1 - i] = temp;
           }
           System.out.println("After: " + Arrays.toString(arr));
       }
   }
   ```

   Output:

   ```
   Before: [2, 9, 4, 7, 1, 6]
   After: [6, 1, 7, 4, 9, 2]
   ```

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>
