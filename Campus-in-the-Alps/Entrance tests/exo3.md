# Exercice 3 - Suite de Syracuse

La Conjecture de Syracuse est une suite définie de la manière suivante : en partant d’un entier n strictement positif, on propose le postulat suivant : 

            si n est impair : n = 3n + 1

            si n est pair : n = n/2

Dès lors que n = 1 on tombe dans une boucle infinie. 1, 4, 2, 1, 4, 2, 1...

 

Écrire une fonction syracuseLength qui donne la longueur de la chaîne de Syracuse pour un entier passé en paramètre. La chaîne se termine dès lors qu’on tombe sur 1. 

Si la fonction reçoit un paramètre inattendu, retourner 0.

```Java
import java.io.*;
import java.util.*;
import java.util.function.*;



public class Main {

    public static int computeSyracuseLength(int input) {

         int length;
         for (length = 0; input != 1; length++) {
            input = (input % 2 == 0) ? input / 2 : 3 * input + 1;
         }
         return length;
    }
    
    
    public static void main(String[] args) throws IOException {
        String input;
        if (args.length > 0) {
            input = args[0];
        } else {
            try (var reader = new BufferedReader(new InputStreamReader(System.in))) {
                input = reader.readLine().trim();
            }
        }
        System.out.println(computeSyracuseLength(Integer.parseInt(input)));
    }

}
```

computeSyracuseLength Method:

java
Copy code
public static int computeSyracuseLength(int input) {
    int length;
    for (length = 0; input != 1; length++) {
        input = (input % 2 == 0) ? input / 2 : 3 * input + 1;
    }
    return length;
}
This method takes an integer input as an argument.
It initializes a variable length to 0.
It uses a for loop to calculate the Syracuse sequence until input becomes 1.
In each iteration, it checks whether input is even or odd using the ternary operator.
If input is even, it divides it by 2; otherwise, it multiplies it by 3 and adds 1.
The loop continues until input becomes 1, and length is incremented in each iteration.
The method returns the length of the Syracuse sequence.