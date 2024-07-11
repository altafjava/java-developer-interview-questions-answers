### Java Developer Realtime Interview Questions & Answers

> Click :star: if you like the project. Pull Request is highly appreciated. Follow me [@AltafJava](https://twitter.com/altafjava) for technical updates.

## Table of Contents

| No. | Questions                                                                                                                                                                                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|     | **Core Java**                                                                                                                                                                                    |
| 1   | [Write an implementation for this funtional interface?](#Write-an-implementation-for-this-funtional-interface)                                                                                   |
| 2   | [Difference between map and flatmap in Java 8?](#Difference-between-map-and-flatmap-in-Java-8)                                                                                                   |
| 3   | [Find the total marks of all students using Java 8 stream.](#Find-the-total-marks-of-all-students-using-Java-8-stream)                                                                           |
| 4   | [Sort the students in descending order based on their marks using Java 8 stream.](#Sort-the-students-in-descending-order-based-on-their-marks-using-Java-8-stream)                               |
| 5   | [What will be the output of the following code?](#What-will-be-the-output-of-the-following-code-5)                                                                                               |
| 6   | [What will be the output of the following code?](#What-will-be-the-output-of-the-following-code-6)                                                                                               |
| 7   | [Find the minimum value from int array.](#Find-the-minimum-value-from-int-array)                                                                                                                 |
|     | **Spring**                                                                                                                                                                                       |
| 1   | [How to read value from custom properties file in spring?](#How-to-read-value-from-custom-properties-file-in-spring)                                                                             |
| 2   | [What is MissingRequestHeaderException?](#What-is-MissingRequestHeaderException)                                                                                                                 |
|     | **Hibernate/JPA**                                                                                                                                                                                |
| 1   | [What is the significance of @Transient annotation?](#What-is-the-significance-of-Transient-annotation)                                                                                          |
| 2   | [What is the N+1 problem in Hibernate?](#What-is-the-N1-problem-in-Hibernate)                                                                                                                    |
| 3   | [Difference between CrudRepository's deleteAllByIds() and JpaRepository's deleteAllByIdsInBatch().](#Difference-between-CrudRepositorys-deleteAllByIds-and-JpaRepositorys-deleteAllByIdsInBatch) |
| 4   | [Differences among Repository, CrudRepository, PagingAndSortingRepository, and JpaRepository.](#Differences-among-Repository-CrudRepository-PagingAndSortingRepository-and-JpaRepository)        |
|     | **Logical**                                                                                                                                                                                      |
| 1   | [Reverse this array without new array.](#Reverse-this-array-without-new-array)                                                                                                                   |
| 2   | [Write a Java program that counts the frequency of each character in a given string.](#Write-a-Java-program-that-counts-the-frequency-of-each-character-in-a-given-string)                       |
| 3   | [Find the length of the longest substring without repeating characters.](#Find-the-length-of-the-longest-substring-without-repeating-characters)                                                 |
| 4   | [Find the longest non-repeating substring in a given string.](#Find-the-longest-non-repeating-substring-in-a-given-string)                                                                       |
| 5   | [Given a list of integers, find the 3rd largest number in O(n) time.](#Given-a-list-of-integers-find-the-3rd-largest-number-in-On-time)                                                          |
| 6   | [Given an array of integers, find all subarrays whose sum is equal to 5.](#Given-an-array-of-integers-find-all-subarrays-whose-sum-is-equal-to-5)                                                |
|     | **Database**                                                                                                                                                                                     |
| 1   | [Write a query to update city in employee table from address table.](#Write-a-query-to-update-city-in-employee-table-from-address-table)                                                         |
| 2   | [Database Question 2](#Database-Question-2)                                                                                                                                                      |
| 3   | [Find duplicate rows from the below shop table.](#Find-duplicate-rows-from-the-below-shop-table)                                                                                                 |
|     | **Apache Kafka**                                                                                                                                                                                 |
| 1   | [Can you explain the internal architecture of Kafka?](#Can-you-explain-the-internal-architecture-of-Kafka)                                                                                       |
| 2   | [How do you manage a Kafka broker failure?](#How-do-you-manage-a-Kafka-broker-failure)                                                                                                           |
| 3   | [Apache Kafka Question 1](#Apache-Kafka-Question-3)                                                                                                                                              |
|     | **Miscellaneous**                                                                                                                                                                                |
| 1   | [What is "Death by a thousand cuts" problem in software development?](#What-is-Death-by-a-thousand-cuts-problem-in-software-development)                                                         |

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

   - **flatMap**: The `flatMap` method transforms each element of a stream into a stream of objects and then combines all those streams into a single stream. It is particularly useful when we want to flatten a stream of collections or arrays into a single stream of elements. The function we pass to the `flatMap()` operation can return an arbitrary number of values for each input, facilitating a one-to-many mapping. This method performs both transformation and flattening, producing a stream of stream values, and is used for both transformation and mapping.

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

7. ### Find the minimum value from int array.

   ```java
   int[] arr = { 2, 9, 4, 7, 1, 6 };
   int min = Arrays.stream(arr).min().getAsInt();
   System.out.println("Minimum value: " + min);
   ```

   Output:

   ```
   Minimum value: 1
   ```

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

## Spring

1. ### How to read value from custom properties file in spring?

   To read values from a custom properties file in Spring, we can use the `@PropertySource` annotation to specify the location of the properties file and the `@Value` annotation to inject the property values into Spring beans.

   **Example:**

   1. **Create a custom properties file (`custom.properties`):**

      ```properties
      app.name=SpringApp
      app.version=1.0
      ```

   2. **Load the custom properties file in Spring configuration class:**

      ```java
      @Configuration
      @PropertySource("classpath:custom.properties")
      public class AppConfig {
          @Value("${app.name}")
          private String appName;

          @Value("${app.version}")
          private String appVersion;

          @Bean
          public AppInfo appInfo() {
              return new AppInfo(appName, appVersion);
          }
      }
      ```

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

2. ### What is MissingRequestHeaderException?

   `MissingRequestHeaderException` is an exception in Spring that is thrown when a required header is missing from an HTTP request. This exception occurs when a controller method expects a specific header to be present in the request but the header is not provided.

   **Example:**

   ```java
   @GetMapping("/user")
   public ResponseEntity<User> getUserDetails(@RequestHeader("Authorization") String token) {
       // Controller logic
   }
   ```

   In the above example, the `getUserDetails` method expects an `Authorization` header to be present in the request. If the `Authorization` header is missing, a `MissingRequestHeaderException` will be thrown.

   To handle this exception, we can use `@ExceptionHandler` in a controller advice or handle it within the controller method itself.

   ```java
   @ExceptionHandler(MissingRequestHeaderException.class)
   public ResponseEntity<String> handleMissingRequestHeaderException(MissingRequestHeaderException ex) {
       return ResponseEntity.status(HttpStatus.BAD_REQUEST).body("Required header is missing: " + ex.getHeaderName());
   }
   ```

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

## Hibernate/JPA

1.  ### What is the significance of @Transient annotation?

    The `@Transient` annotation in JPA is used to indicate that a field or property should not be persisted to the database. When an entity class is mapped to a database table, all its fields are persisted by default. However, there may be scenarios where certain fields should not be stored in the database, such as derived or transient fields that are calculated at runtime.

    **Example:**

    ```java
    import javax.persistence.Transient;
    @Entity
    public class Employee {
        @Id
        private Long id;
        private String name;
        @Transient
        private int age;
        // Getters and setters
    }
    ```

    In the above example, the `age` field is marked with the `@Transient` annotation, indicating that it should not be persisted to the database. The `age` field is considered transient and will not be included in the database schema when the `Employee` entity is mapped to a database table. The `@Transient` annotation can be applied to fields, properties, or methods in an entity class to exclude them from database persistence.

    **Examples:**

    1. _Calculated Fields:_ Sometimes, we might have fields whose values are calculated based on other persisted fields. These calculated fields do not need to be stored in the database because their values can be derived at runtime.

       ```java
       @Entity
       public class Order {
           @Id
           private Long id;
           private BigDecimal price;
           private BigDecimal taxRate;
           @Transient
           private BigDecimal totalPrice; // Calculated as price + (price * taxRate)

           public BigDecimal getTotalPrice() {
               return price.add(price.multiply(taxRate));
           }
       }
       ```

    2. _Logging or Debugging Information:_ Fields used for logging or debugging purposes, which are useful during development or troubleshooting but do not need to be part of the persistent state.

       ```java
       @Entity
       public class User {
           @Id
           private Long id;
           private String username;
           @Transient
           private String debugMessage; // Used only for debugging, not persisted
       }
       ```

    3. _Security or Sensitive Information:_ Sometimes, you might want to temporarily hold sensitive information like passwords or tokens in an entity for processing or validation, but you do not want these details to be stored in the database.

       ```java
       @Entity
       public class Account {
           @Id
           private Long id;
           private String accountName;

           @Transient
           private String temporaryAuthToken; // Sensitive information not to be persisted
       }
       ```

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

2.  ### What is the N+1 problem in Hibernate?

    The N+1 problem is a common performance issue that occurs when using an ORM framework like Hibernate to fetch data from a relational database. It arises when an entity is associated with a collection of child entities (one-to-many or many-to-many relationship), and the ORM framework generates N+1 SQL queries to fetch the associated child entities.

    **Example:**

    Consider the following entities `Author` and `Book` with a one-to-many relationship:

    ```java
    @Entity
    public class Author {
        @Id
        private Long id;
        private String name;
        @OneToMany(mappedBy = "author", cascade = CascadeType.ALL)
        private List<Book> books;
    }

    @Entity
    public class Book {
        @Id
        private Long id;
        private String title;
        @ManyToOne
        private Author author;
    }
    ```

    If we fetch a list of authors along with their books using Hibernate, the N+1 problem occurs when Hibernate executes N+1 SQL queries to fetch the associated books for each author. For example, if there are 10 authors, Hibernate will execute 1 query to fetch the authors and then 10 additional queries to fetch the books for each author, resulting in a total of 11 queries (N+1).

    **Solution:**

    To avoid the N+1 problem in Hibernate, we can use fetch strategies like `FetchType.EAGER`, `JOIN FETCH` or `@BatchSize` to fetch the associated entities eagerly or in batches. By specifying the fetch strategy in the query or mapping annotations, we can optimize the data retrieval process and reduce the number of SQL queries executed by Hibernate.

    **Example:**

    1. **Using FetchType.EAGER:**

       ```java
       @Entity
       public class Author {
           @Id
           private Long id;
           private String name;
           @OneToMany(mappedBy = "author", cascade = CascadeType.ALL)
           private List<Book> books;
       }
       ```

    2. **Using JOIN FETCH:**

       ```java
       List<Author> authors = entityManager.createQuery("SELECT a FROM Author a JOIN FETCH a.books", Author.class).getResultList();
       ```

    3. **Using @BatchSize:**

       ```java
       @OneToMany(mappedBy = "author", cascade = CascadeType.ALL)
       @BatchSize(size = 10)
       private List<Book> books;
       ```

    By using appropriate fetch strategies and tuning the mappings, we can mitigate the N+1 problem in Hibernate and improve the performance of data retrieval operations.

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

3.  ### Difference between CrudRepository's deleteAllByIds() and JpaRepository's deleteAllByIdsInBatch().

    Both `CrudRepository` and `JpaRepository` interfaces in Spring Data provide methods for deleting entities by their IDs. However, there are differences in the behavior and performance of the `deleteAllByIds()` method in `CrudRepository` and the `deleteAllByIdsInBatch()` method in `JpaRepository`.

    - **CrudRepository's deleteAllByIds():**

      - The `deleteAllByIds()` method in `CrudRepository` deletes entities one by one in a loop, resulting in multiple individual delete queries being executed for each ID.
      - This method is suitable for deleting a small number of entities or when the number of entities to be deleted is not known in advance.
      - It is less efficient for bulk deletion operations as it generates multiple delete queries, leading to increased database round trips and performance overhead.
      - If the provided id is not present in the database, it will throw `EmptyResultDataAccessException`.

      ```java
      public interface UserRepository extends CrudRepository<User, Long> {
            void deleteAllByIds(List<Long> ids);
      }
      ```

    - **JpaRepository's deleteAllByIdsInBatch():**

      - The `deleteAllByIdsInBatch()` method in `JpaRepository` performs batch deletion of entities using a single delete query with an `IN` clause containing the list of IDs to be deleted.
      - This method is optimized for bulk deletion operations and is more efficient than `deleteAllByIds()` for deleting a large number of entities.
      - It reduces the number of database round trips and improves performance by executing a single batch delete query for all the specified IDs.
      - If the provided id not present in the database, it will not throw any exception.

      ```java
      public interface UserRepository extends JpaRepository<User, Long> {
            @Modifying
            @Query("DELETE FROM User u WHERE u.id IN :ids")
            void deleteAllByIdsInBatch(@Param("ids") List<Long> ids);
      }
      ```

    - **Usage:**
      - Use `deleteAllByIds()` in `CrudRepository` for deleting a small number of entities or when the number of entities to be deleted is not large.
      - Use `deleteAllByIdsInBatch()` in `JpaRepository` for bulk deletion of entities when deleting a large number of entities efficiently.

    By choosing the appropriate method based on the number of entities to be deleted and the performance requirements, we can optimize the deletion process and improve the efficiency of bulk deletion operations in Spring Data repositories.

    <div align="right">
         <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

4.  ### Differences among Repository, CrudRepository, PagingAndSortingRepository, and JpaRepository.

    - **Repository Interface:**

      - The `Repository` interface is the base interface for all Spring Data repositories.
      - It is a marker interface and does not provide any methods.
      - It is used to enable the Spring Data infrastructure to detect repository interfaces and create their implementations.

    - **CrudRepository Interface:**

      - The `CrudRepository` interface extends the `Repository` interface and provides generic CRUD (Create, Read, Update, Delete) operations for entity classes.
      - It includes methods like:
        - `save(S entity)`: Saves a given entity.
        - `saveAll(Iterable<S> entities)`: Saves all given entities.
        - `findById(ID id)`: Retrieves an entity by its ID.
        - `existsById(ID id)`: Checks if an entity exists by its ID.
        - `findAll()`: Returns all entities.
        - `findAllById(Iterable<ID> ids)`: Returns all entities with the given IDs.
        - `count()`: Returns the count of entities.
        - `deleteById(ID id)`: Deletes an entity by its ID.
        - `delete(T entity)`: Deletes a given entity.
        - `deleteById(Iterable<? extends ID> ids)`: Deletes all entities with the given IDs.
        - `deleteAll(Iterable<? extends S> entities)`: Deletes all given entities.
        - `deleteAll()`: Deletes all entities.

    - **PagingAndSortingRepository Interface:**

      - The `PagingAndSortingRepository` interface extends the `CrudRepository` interface and provides additional methods for pagination and sorting of query results.
      - It includes methods like:
        - `findAll(Sort sort)`: Returns all entities sorted by the given options.
        - `findAll(Pageable pageable)`: Returns a `Page` of entities meeting the paging restriction provided in the `Pageable` object.

    - **JpaRepository Interface:**

      - The `JpaRepository` interface extends the `PagingAndSortingRepository` interface and provides JPA-specific operations.
      - It includes all the methods of `CrudRepository` and `PagingAndSortingRepository` and adds JPA-specific methods such as:
        - `saveAndFlush(S entity)`: Saves an entity and flushes changes instantly.
        - `deleteAllInBatch(Iterable<T> entities)`: Deletes all entities in a batch.
        - `deleteAllByIdInBatch(Iterable<T> ids)`: Deletes all entities with the given IDs in a batch.
        - `deleteAllInBatch()`: Deletes all entities in a batch.
        - `getOne(ID id)`: Retrieves a reference to the entity with the given ID.
        - `findAll()`: Returns all entities.
        - `findAll(Sort sort)`: Returns all entities sorted by the given options.
        - `findAllById(Iterable<ID> ids)`: Returns all entities with the given IDs.

    **Scenarios for Choosing Each Interface**:

    - Use `Repository` if we only need to mark an interface as a repository without any specific methods.
    - Use `CrudRepository` for basic CRUD operations without the need for pagination or sorting.
    - Use `PagingAndSortingRepository` when we need to retrieve entities with pagination and sorting capabilities.
    - Use `JpaRepository` when we require advanced JPA-specific features in addition to CRUD operations, pagination, and sorting.

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

    To find the 3rd largest number in a list of integers with O(n) running time complexity in Java, we can use a single pass algorithm. The idea is to traverse the list once and keep track of the top three largest unique numbers using three variables. At the end of the traversal, the third-largest number will be stored in the third variable.

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

6.  ### Given an array of integers, find all subarrays whose sum is equal to 5.

    To find all subarrays in an array of integers whose sum is equal to a given target sum (e.g., 5), we can use a sliding window approach. The idea is to maintain a window that expands and contracts based on the sum of elements within the window. We can use two pointers (start and end) to represent the window and move them accordingly to find subarrays with the desired sum.

    ```java
    public static void findSubarraysWithSum(int[] arr, int targetSum) {
        int start = 0, end = 0, sum = 0;
        while (end < arr.length) {
            sum += arr[end];
            while (sum > targetSum) {
                sum -= arr[start];
                start++;
            }
            if (sum == targetSum) {
                System.out.println("Subarray with sum 5 found: " + Arrays.toString(Arrays.copyOfRange(arr, start, end + 1)));
            }
            end++;
        }
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 2, 1, 4, 1};
        int targetSum = 5;
        findSubarraysWithSum(arr, targetSum);
    }
    ```

    Output:

    ```
    Subarray with sum 5 found: [2, 3]
    Subarray with sum 5 found: [3, 2]
    Subarray with sum 5 found: [1, 4]
    Subarray with sum 5 found: [4, 1]
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

3. ### Find duplicate rows from the below shop table.
   ```
   id | name    | category
   ---|---------|---------
   1  | steak   | meat
   2  | cake    | sweets
   3  | steak   | meat
   4  | chicken | meat
   5  | cake    | sweets
   6  | cake    | sweets
   ```
   **Answer:**
   ```sql
   SELECT name, category, COUNT(*)
   FROM shop
   GROUP BY name, category
   HAVING COUNT(*) > 1;
   ```
   Output:
   ```
   name | category | count
   -----|----------|------
   steak| meat     | 2
   cake | sweets   | 3
   ```
   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

## Apache Kafka

1. ### Can you explain the internal architecture of Kafka?

   Apache Kafka is a distributed streaming platform that is designed to handle large-scale data processing (with high throughput, fault tolerance, and scalability) and real-time event streaming. The internal architecture of Kafka consists of several key components that work together to provide high throughput, fault tolerance, and scalability. Here is an overview of the internal architecture of Kafka:

   1. **Broker:** A Kafka cluster consists of one or more brokers, which are individual servers that store and manage topics and partitions. Each broker is responsible for handling client requests, storing data, and replicating data across the cluster.

      - _Leader and Follower_: For each partition, one broker is elected as the leader, and one or more brokers are followers. The leader handles all read and write requests, while followers replicate the data to ensure fault tolerance.

   2. **Topic:** A topic is a logical channel to which data is sent and from which data is read. Topics are categories or feed names to which messages are published. Topics are divided into partitions to allow for parallel processing and distribution of messages across multiple brokers.

   3. **Partition:** Each topic is split into multiple partitions. Partitions allow Kafka to scale horizontally and provide parallelism. Each partition is an ordered, immutable sequence of records that are continually appended.

   4. **Producer:** Producers are client applications that send records to a Kafka topic. Producers can choose which partition to send records to within a topic (usually using a key for partitioning).

      - _Acknowledgment_: Producers can choose to receive acknowledgments from brokers after successfully writing messages to Kafka. Acknowledgments can be synchronous or asynchronous, depending on the desired level of reliability.

   5. **Consumer:** Consumers are client applications that subscribe to topics and consume messages from Kafka partitions. Consumers read messages from partitions in the order they were produced. Consumers can be part of a consumer group, where each record is delivered to one consumer in the group, ensuring load balancing and fault tolerance.

      - _Consumer Group_: A consumer group is a group of consumers that work together to consume messages from one or more topics. Each consumer in a group is assigned a subset of partitions to read from, enabling parallel processing and load balancing.
      - _Offset Management_: Consumers track their progress by storing the offset of the last message they have read, allowing them to resume reading from the correct position after a restart.
      - _Consumer Rebalancing_: Kafka automatically rebalances partitions among consumers in a consumer group when new consumers join or existing consumers leave the group.
      - _Consumer Offset Commitment_: Consumers can commit offsets to Kafka to indicate that they have successfully processed messages. This allows consumers to resume reading from the last committed offset in case of failure.

   6. **ZooKeeper:** ZooKeeper is used by Kafka for cluster coordination, metadata management, and leader election. ZooKeeper maintains information about brokers, topics, partitions, and consumer groups, ensuring consistency and synchronization across the Kafka cluster.

   7. **Replication:** Kafka uses replication to ensure fault tolerance and data durability. Each partition is replicated across multiple brokers, with one broker serving as the leader and the others as followers. Replication allows Kafka to recover from broker failures and maintain data availability.

      - _In-Sync Replicas (ISR)_: Kafka maintains a set of in-sync replicas (ISRs) for each partition, which are replicas that are up-to-date with the leader. ISRs are used to ensure data consistency and fault tolerance.

   8. **Log Segments:** Kafka stores messages in log segments, which are sequential files on disk. Each partition consists of multiple log segments, and older log segments are periodically compacted and deleted to manage disk space efficiently.

   9. **Offset:** An offset is a unique identifier assigned to each message within a partition. Consumers track their progress by storing the offset of the last message they have read, allowing them to resume reading from the correct position after a restart.

   10. **Controller:** One of the brokers in a Kafka cluster is designated as the controller. The controller is responsible for administrative tasks like partition assignment, leader election, and reassigning partitions in case of broker failures. The controller ensures the overall health and stability of the Kafka cluster. If the controller fails, another broker is elected as the new controller.

   ```
                 +-------------------------+
                 |       ZooKeeper         |
                 +-----------+-------------+
                             |
                             |
                             v
         +-------------------+--------------------+
         |         Kafka Cluster (Brokers)        |
         |                                        |
         | +---------+   +---------+   +---------+ |
         | | Broker 1|   | Broker 2|   | Broker 3| |
         | +----+----+   +----+----+   +----+----+ |
         |      |             |             |      |
         +------+-------------+-------------+------+
                |             |             |
        +-------v------+ +----v-------+ +---v-------+
        |   Topic A    | |  Topic B   | |  Topic C  |
        +--------------+ +------------+ +-----------+
        | Part. 0 | Part. 1 | Part. 2 | Part. 0 | ... |
        +---------+ +-------+ +-------+ +-------+-----+

   ```

    <div align="right">
        <b><a href="#table-of-contents">⬆ Back to Top</a></b>
    </div>

2. ### How do you manage a Kafka broker failure?

   Managing a Kafka broker failure involves taking appropriate steps to ensure the availability and reliability of the Kafka cluster. When a broker fails, it can impact the overall performance and data replication of the cluster. Here are some strategies to manage a Kafka broker failure:

   1. **Monitoring and Alerting:** Implement monitoring tools to detect broker failures and set up alerts to notify administrators when a broker goes down. Monitoring tools can track metrics like CPU usage, memory consumption, disk space, and network traffic to identify potential issues.

      _Example:_ Prometheus, Grafana, Nagios, Datadog.

   2. **Replication Factor:** Configure the replication factor for topics to ensure data redundancy across multiple brokers. By setting a replication factor of at least 2 or 3, Kafka can maintain multiple copies of data across brokers, allowing for data recovery in case of a broker failure.

   3. **Broker Reassignment:** If a broker fails, Kafka can automatically reassign the partitions hosted on the failed broker to other healthy brokers in the cluster. This process is known as partition reassignment and helps maintain data availability and fault tolerance.

   4. **Broker Replacement:** In the event of a permanent broker failure, replace the failed broker with a new broker to restore the cluster's capacity and performance. The replacement broker should have the same configuration and storage capacity as the failed broker to maintain consistency.

   5. **Data Recovery:** If data loss occurs due to a broker failure, Kafka can recover data from the replicated partitions on other brokers. By leveraging the replication factor and data retention policies, Kafka can restore lost data and maintain data integrity.

   6. **Cluster Scaling:** To prevent performance degradation during a broker failure, scale the Kafka cluster horizontally by adding more brokers. A larger cluster with additional brokers can distribute the workload and improve fault tolerance, reducing the impact of individual broker failures.

   7. **Backup and Disaster Recovery:** Implement backup and disaster recovery strategies to protect data in case of catastrophic failures. Regularly back up Kafka data and configurations, and establish disaster recovery procedures to restore the cluster in the event of a major outage.

   <div align="right">
       <b><a href="#table-of-contents">⬆ Back to Top</a></b>
   </div>

3. ### Apache Kafka Question 3

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
