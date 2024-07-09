### Java Developer Realtime Interview Questions & Answers

> Click :star: if you like the project. Pull Request is highly appreciated. Follow me [@AltafJava](https://twitter.com/altafjava) for technical updates.

## Table of Contents

| No. | Questions                                                                                                                                                                  |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|     | **Core Java**                                                                                                                                                              |
| 1   | [Write an implementation for this funtional interface?](#Write-an-implementation-for-this-funtional-interface)                                                             |
| 2   | [Difference between map and flatmap in Java 8?](#Difference-between-map-and-flatmap-in-Java-8)                                                                             |
| 3   | [Find the total marks of all students using Java 8 stream.](#Find-the-total-marks-of-all-students-using-Java-8-stream)                                                     |
| 4   | [Sort the students in descending order based on their marks using Java 8 stream.](#Sort-the-students-in-descending-order-based-on-their-marks-using-Java-8-stream)         |
| 5   | [What will be the output of the following code?](#What-will-be-the-output-of-the-following-code-5)                                                                         |
| 6   | [What will be the output of the following code?](#What-will-be-the-output-of-the-following-code-6)                                                                         |
|     | **Logical**                                                                                                                                                                |
| 1   | [Reverse this array without new array.](#Reverse-this-array-without-new-array)                                                                                             |
| 2   | [Write a Java program that counts the frequency of each character in a given string.](#Write-a-Java-program-that-counts-the-frequency-of-each-character-in-a-given-string) |
| 3   | [Find the length of the longest substring without repeating characters.](#Find-the-length-of-the-longest-substring-without-repeating-characters)                           |
| 4   | [Find the longest non-repeating substring in a given string.](#Find-the-longest-non-repeating-substring-in-a-given-string)                                                 |
| 5   | [Given a list of integers, find the 3rd largest number in O(n) time.](#Given-a-list-of-integers-find-the-3rd-largest-number-in-On-time)                                    |
|     | **Database**                                                                                                                                                               |
| 1   | [Write a query to update city in employee table from address table.](#Write-a-query-to-update-city-in-employee-table-from-address-table)                                   |
| 2   | [Database Question 2](#Database-Question-2)                                                                                                                                |
|     | **Apache Kafka**                                                                                                                                                           |
| 1   | [Apache Kafka Question 1](#Apache-Kafka-Question-1)                                                                                                                        |
|     | **Miscellaneous**                                                                                                                                                          |
| 1   | [What is "Death by a thousand cuts" problem in software development?](#What-is-Death-by-a-thousand-cuts-problem-in-software-development)                                   |

## Core Java

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
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
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

1.  ### Reverse this array without new array.

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

2.  ### Write a Java program that counts the frequency of each character in a given string.

    ```java
     String str = "programming";
     Map<Character, Integer> charFrequency = new HashMap<>();
     for (char c : str.toCharArray()) {
         charFrequency.put(c, charFrequency.getOrDefault(c, 0) + 1);
     }
     System.out.println(charFrequency);
    ```

    **Using Java 8 Stream API:**

    ```java
     String str = "programming";
     Map<Character, Long> charFrequency = str.chars()
             .mapToObj(c -> (char) c)
             .collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));
     System.out.println(charFrequency);
    ```

    Output:

    ```
    {p=1, r=2, o=1, g=2, a=1, m=2, i=1, n=1}
    ```

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

3.  ### Find the length of the longest substring without repeating characters.

    ```java
    public static String lengthOflongestNonRepeatingSubstring(String str) {
        int max = 0;
        Map<Character, Integer> map = new LinkedHashMap<>();
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (map.containsKey(ch)) {
                i = map.get(ch);
                map.clear();
            } else {
                map.put(ch, i);
            }
            max = Math.max(max, map.size());
        }
        return max;
    }
    ```

    ```java
    String str = "abcabcbb";
    System.out.println(lengthOflongestNonRepeatingSubstring(str));
    ```

    Output:

    ```
    3
    ```

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

4.  ### Find the longest non-repeating substring in a given string.

    ```java
    public static String longestNonRepeatingSubstring(String str) {
        int maxLength = 0;
         int start = 0;
         String longestSubstring = "";
         Map<Character, Integer> map = new HashMap<>();
         for (int i = 0; i < str.length(); i++) {
             char ch = str.charAt(i);
             if (map.containsKey(ch)) {
                 start = Math.max(start, map.get(ch) + 1);
             }
             map.put(ch, i);
             if (i - start + 1 > maxLength) {
                 maxLength = i - start + 1;
                 longestSubstring = str.substring(start, i + 1);
             }
         }
         return longestSubstring;
    }
    ```

    ```java
    String str = "abcabcbb";
    System.out.println(longestNonRepeatingSubstring(str));
    ```

    Output:

    ```
    abc
    ```

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

5.  ### Given a list of integers, find the 3rd largest number in O(n) time.

    To find the 3rd largest number in a list of integers with O(n) running time complexity in Java, you can use a single pass algorithm. The idea is to traverse the list once and keep track of the top three largest unique numbers using three variables. At the end of the traversal, the third-largest number will be stored in the third variable.

    ```java
    public static void main(String[] args) {
        int[] arr = { 8, 7, 2, 1, 0, 9, 6 };
        int kthLargest = findThirdLargest(arr);
        System.out.println("3rd largest element is: " + kthLargest);
    }

    public static int findThirdLargest(int[] nums) {
        int first = Integer.MIN_VALUE, second = Integer.MIN_VALUE, third = Integer.MIN_VALUE;
        for (int num : nums) {
            if (num > first) {
                third = second;
                second = first;
                first = num;
            } else if (num > second && num < first) {
                third = second;
                second = num;
            } else if (num > third && num < second) {
                third = num;
            }
        }
        return third;
    }
    ```

    Output:

    ```
    3rd largest element is: 7
    ```

    If we want to find the kth largest element in an array, we can use the QuickSelect algorithm, which is an efficient selection algorithm based on the partitioning technique of the quicksort algorithm.

    ```java
    public static void main(String[] args) {
        int[] arr = { 8, 7, 2, 1, 0, 9, 6 };
        int k = 3; // To find the 3rd largest number
        int kthLargest = quickSelect(arr, 0, arr.length - 1, arr.length - k);
        System.out.println(k + "th largest element is: " + kthLargest);
    }

    private static int quickSelect(int[] arr, int low, int high, int k) {
        if (low <= high) {
            int partitionIndex = partition(arr, low, high);
            if (partitionIndex == k) {
                return arr[partitionIndex];
            } else if (partitionIndex < k) {
                return quickSelect(arr, partitionIndex + 1, high, k);
            } else {
                return quickSelect(arr, low, partitionIndex - 1, k);
            }
        }
        return Integer.MIN_VALUE; // This should never hit if k is within the bounds of the array
    }

    private static int partition(int[] arr, int low, int high) {
        int pivot = arr[low];
        int i = low, j = high;
        do {
            while (i <= high && arr[i] <= pivot) {
                i++;
            }
            while (arr[j] > pivot) {
                j--;
            }
            if (i < j) {
                swap(arr, i, j);
            }
        } while (i < j);
        swap(arr, low, j);
        return j;
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
    ```

    Output:

    ```
    3th largest element is: 7
    ```

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

## Database

1. ### Write a query to update city in employee table from address table.

   ```sql
   Employee Table
   id
   name
   city

   Address Table
   id
   city
   ```

   **Answer**:

   ```sql
   UPDATE employee e
   JOIN address a ON e.id = a.id
   SET e.city = a.city;
   ```

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

2. ### Database Question 2

   **Question:** Given an Employees table with columns first_name, last_name, and salary, write an SQL query to find all employees who have a salary greater than any employee with the first name 'Nawab'.

   ```sql
   SELECT * FROM Employees
   WHERE salary > (SELECT MAX(salary) FROM Employees WHERE first_name = 'Nawab');
   ```

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

## Apache Kafka

1. ### Apache Kafka Question 1

   **Question:**
   A Kafka topic has 100 messages distributed equally across 10 partitions. If there are only 4 consumers subscribed to this topic, explain how the messages will be consumed by the consumers. How will Kafka manage the distribution of partitions among the consumers?

   **Answer:**

   _Partition Assignment:_ Kafka will distribute the partitions among the 4 consumers as evenly as possible. Since there are 10 partitions, the most even distribution will have 2 consumers consuming from 3 partitions each, and the other 2 consumers consuming from 2 partitions each.

   _Message Consumption:_ Each consumer will independently consume messages from the partitions assigned to it. Given the messages are evenly distributed, each partition has 10 messages, leading to a scenario where 2 consumers will process 30 messages each (from 3 partitions), and the other 2 consumers will process 20 messages each (from 2 partitions).

   _Parallel Processing:_ All 4 consumers will process their assigned messages in parallel, increasing the throughput and efficiency of message processing compared to having a single consumer.

   _Consumer Group Coordination:_ Kafka ensures that within a consumer group, each partition is only consumed by one consumer, preventing duplicate processing of messages. If a consumer fails or is added to the group, Kafka will rebalance the partitions among the available consumers to ensure continued parallel processing.

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

## Miscellaneous

1. ### What is "Death by a thousand cuts" problem in software development?

   "Death by a thousand cuts" is a metaphor used in software development to describe the accumulation of small, seemingly insignificant issues or problems that, when combined, can lead to significant negative consequences or failure of a project. These small issues, if left unaddressed, can gradually erode the quality, performance, or maintainability of the software, resulting in a situation where the software becomes increasingly difficult to maintain, enhance, or scale. The term highlights the importance of addressing minor issues promptly and maintaining a focus on quality throughout the development process to prevent the accumulation of problems that can lead to project failure. It emphasizes the need for attention to detail, proactive issue resolution, and continuous improvement to avoid the "death by a thousand cuts" scenario.

   **Example:** Ignoring code quality, not following coding standards, not addressing technical debt, lack of code reviews, not fixing bugs promptly, etc. can contribute to the "death by a thousand cuts" problem.

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>
