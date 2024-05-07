### Java Developer Realtime Interview Questions & Answers

> Click :star: if you like the project. Pull Request is highly appreciated. Follow me [@AltafJava](https://twitter.com/altafjava) for technical updates.

## Table of Contents

| No. | Questions                                                                                                      |
| --- | -------------------------------------------------------------------------------------------------------------- |
|     | **Core**                                                                                                       |
| 1   | [Write an implementation for this funtional interface?](#Write-an-implementation-for-this-funtional-interface) |
| 2   | [Difference between map and flatmap in Java 8?](#Difference-between-map-and-flatmap-in-Java-8?)                |
|     | **Logical**                                                                                                    |
| 1   | [Reverse this array without new array.](#Reverse-this-array-without-new-array)                                 |

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
        <b><a href="#core">⬆ Back to Top</a></b>
    </div>

2. Difference between map and flatmap in Java 8?

    In Java 8, `map` and `flatMap` are both methods in the Stream interface used for transforming elements.

    - **map**: The `map` method transforms each element of a stream into another object using the provided function. It applies the function to each element of the stream independently and returns a new stream containing the transformed elements.

        ```java
        List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);
        List<Integer> mapResult = list.stream().map(x -> x * 2).collect(Collectors.toList());
        System.out.println(mapResult); // prints [2, 4, 6, 8, 10]
        ```

    - **flatMap**: The `flatMap` method transforms each element of a stream into a stream of objects and then combines all the streams into a single stream. It is useful when we want to flatten a stream of collections or arrays into a single stream of elements.

        ```java
        List<List<Integer>> list = Arrays.asList(Arrays.asList(1, 2), Arrays.asList(3, 4), Arrays.asList(5, 6));
        List<Integer> flatMapResult = list.stream().flatMap(Collection::stream).collect(Collectors.toList());
        System.out.println(flatMapResult); // prints [1, 2, 3, 4, 5, 6]
        ```

    <div align="right">
        <b><a href="#core">⬆ Back to Top</a></b>
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
        <b><a href="#logical">⬆ Back to Top</a></b>
    </div>
