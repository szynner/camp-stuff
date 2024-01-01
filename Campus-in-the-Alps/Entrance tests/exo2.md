# Exercice 2 - Palindrome

Écrire une fonction qui indique si la chaîne de caractères passée en paramètre est un palindrome ou non.

Un palindrome est une phrase dite "miroir" qui peut être lue dans un sens ou un autre. Par exemple : « lol », « race car », ou encore « Engage le jeu, que je le gagne. ». On notera ici que les espaces et les majuscules n’ont pas d’impact.

Dans cette première version de l’algorithme, on ne prendra en compte que les caractères représentant un chiffre ou une lettre non accentuée ; les autres caractères seront ignorés.  Deux caractères représentant la même lettre en majuscule et minuscule sont considérés comme identiques.

```Java
import java.io.*;
import java.util.*;
import java.util.function.*;



public class Main {

    public static boolean isPalindrome(String input){

    char[] charArray = input.toCharArray();
    int start = 0;
    int end = input.length() - 1;

    while(start < end) {
        if(charArray[start] != charArray[end]) {
            return false;
        }
        start ++;
        end --;
    }
    return true;
}
    
    
    public static void main(String[] args) throws IOException {
        String input;
        if (args.length > 0) {
            input = args[0];
        } else {
            try (var reader = new BufferedReader(new InputStreamReader(System.in))) {
                input = reader.readLine();
            }
        }
        System.out.println(isPalindrome(input));
    }

}
```

# How to


```Java
public class Main {
```

This line declares a class named `Main`. It does not use the `public` modifier, which means that the class is accessible only within the same package.


```Java
    public static boolean isPalindrome(String input){
```

This line declares a public, static method named `isPalindrome` that takes a string (`String` named `input`) as a parameter and returns a boolean value (`true` if the input is a palindrome, `false` otherwise).

```Java
    char[] charArray = input.toCharArray();
```

This line converts the input string into an array of characters. This is done using the `toCharArray` method of the `String` class.

```Java
    int start = 0;
    int end = input.length() - 1;
```

These lines initialize two integer variables, `start` and `end`. `start` is set to 0, and `end` is set to the last index of the input string.

```Java
    while(start < end) {
```

This line starts a while loop that continues as long as the `start` index is less than the `end` index.

```Java
        if(charArray[start] != charArray[end]) {
```

Inside the while loop, this line checks if the character at the `start` index is not equal to the character at the `end` index. If they are not equal, the method returns `false`, indicating that the input string is not a palindrome.

```Java
            return false;
        }
```

If the condition in the `if` statement is true, this line is executed, and the method returns `false`.

```Java
        start ++;
        end --;
    }
```

These lines increment the `start` index and decrement the `end` index in each iteration of the while loop, moving towards the center of the string.


```Java
    return true;
```

If the while loop completes without encountering a mismatch, it means the input string is a palindrome, and this line returns `true`.


```Java
}
```

This closing brace marks the end of the `isPalindrome` method and the end of the `Main` class.

In summary, the `isPalindrome` method checks if a given string is a palindrome by comparing characters from the beginning and end of the string, moving towards the center. If any characters do not match, the method returns `false`; otherwise, it returns `true`.