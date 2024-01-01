# Exercice 1 - Nombre d'entiers pairs

Écrire une fonction qui prend en entrée une collection d’entiers et retourne le nombre d’entiers pairs dans cette collection.

```Java
import java.io.*;
import java.util.*;
import java.util.function.*;



public final class Main {

    public static int countEvenNumber(int[] input) {
      int numCount = 0;
        for (int Number : input) {
           if (Number % 2 == 0) {
              numCount++;
           }
        }
        return numCount;
    }
  
  
    
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            try (var reader = new BufferedReader(new InputStreamReader(System.in))) {
                args = reader.readLine().split("\\s|,");
            }
        }
        int[] input = Arrays.stream(args)
                .filter(Predicate.not(String::isBlank))
                .mapToInt(Integer::parseInt)
                .toArray();
        System.out.println(countEvenNumber(input));
    }
    
}
```

# How it works


```java
public final class Main {
```

This line declares a public and final class named Main. The final keyword means that the class cannot be extended (i.e., no other class can inherit from it).



```java
    public static int countEvenNumber(int[] input) {
```

This line declares a public, static method named `countEvenNumber` that takes an array of integers (`int[]` named `input`) as a parameter. The method returns an integer (`int`).

```java
      int numCount = 0;
```

This line declares and initializes an integer variable named `numCount` with a value of 0. This variable will be used to count the number of even numbers in the array.


```Java
        for (int Number : input) {
```

This line starts a for-each loop that iterates over each element (`Number`) in the array `input`.


```java
           if (Number % 2 == 0) {
```

This line checks if the current element (`Number`) is an even number. The `%` operator is the modulus operator, and `Number % 2 == 0` checks if `Number` is divisible evenly by 2, indicating that it's an even number.


```Java
              numCount++;
```

If the current element is an even number, this line increments the `numCount` variable by 1.


```Java
           }
        }
```

This block of code is the body of the for-each loop. It contains the condition for checking even numbers and the increment statement. It iterates through all elements in the array.

```Java
        return numCount;
```
After the for-each loop, this line returns the final count of even numbers (`numCount`) from the method.

```Java
    }
```
This closing brace marks the end of the `countEvenNumber` method.

In summary, the `countEvenNumber` method takes an array of integers as input, iterates through each element, checks if the element is even, and counts the number of even elements. The final count is then returned.