# Exercice 4 - Intégrité d'une chaîne de caractères

Un algorithme de clé de Luhn est un procédé permettant de créer une “clé de sécurité” intégrée à la fin de la donnée à certifier permettant ainsi d’en confirmer la validité. Ce procédé est utilisé par exemple pour la vérification d’un numéro de sécurité sociale, d’un IBAN, d’une carte bancaire... L’algorithme ayant une forme particulière, on décide de créer une version alternative améliorée du système. 
 

Dans cet exercice, l’objectif est de créer une fonction verifyIntegrity qui prend en paramètre une chaîne de caractères, et renvoie un booléen : true si la clé est valide, false si elle n’est pas valide. 


Le numéro passé en paramètre est valide si : 

Le numéro à valider fait 13 chiffres, et le dernier chiffre est la clé.
Pour calculer la clé il faut : 
x1 : prendre les nombres en position 1, 3, 5, 7, 9 et 11 et les additionner tous.
x2 : prendre les nombres en position 2, 4, 6, 8, 10 et 12, les multiplier par 3 et les additionner tous.
x : additionner les 2 valeurs (x1, et x2) calculées précédemment
y : calculer le modulo 10 de x
si y vaut 0, la clé est : 0
sinon la clé est : 10 - y

```Java
import java.io.*;
import java.util.*;

public class Main {

    public static boolean verifyIntegrity(String input) {

        if (input.length() != 13) {
            return false;
        }

        int[] n = new int[13];

        // Convert input string to array of integers
        for (int i = 0; i < 13; i++) {
            n[i] = Character.getNumericValue(input.charAt(i));
        }

        int x1 = n[0] + n[2] + n[4] + n[6] + n[8] + n[10];
        int x2 = n[1] * 3 + n[3] * 3 + n[5] * 3 + n[7] * 3 + n[9] * 3 + n[11] * 3;

        int x = x1 + x2;
        int y = x % 10;

        int key;
        if (y == 0) {
            key = 0;
        } else {
            key = 10 - y;
        }

        return key == n[12];
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
        System.out.println(verifyIntegrity(input));
    }
}
```