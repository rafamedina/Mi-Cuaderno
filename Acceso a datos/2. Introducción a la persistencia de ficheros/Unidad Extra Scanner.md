Permite leer cadenas de texto tanto valores numéricos sin necesidad de hacer conversiones manuales.

## Metodos

next() le la siguiente palabra ahsta espacio
nextLine() lee una linea completa
nextInt() lee un numero
nextDouble() lee un numero decimal
hasNext() devuelve true si hay mas datos disponibles
close() 



## Leer datos desde teclado 
```java
import java.util.Scanner;

public class EjemploScanner {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Introduce tu nombre: ");
        String nombre = sc.nextLine();

        System.out.print("Introduce tu edad: ");
        int edad = sc.nextInt();

        System.out.println("Hola " + nombre + ", tienes " + edad + " años.");

        sc.close(); // Siempre cerrar al final
    }
}
```


### Ventajas frente a otras clases de lectura de archivos

- `Scanner` permite **leer tokens individuales** (palabras, números, etc.) fácilmente.
    
- Se pueden aplicar **separadores personalizados** con el método `useDelimiter()`.
    
- Sin embargo, para archivos muy grandes, `BufferedReader` suele ser más eficiente.

## Creación de menús interactivos con Scanner


```java
import java.util.Scanner;

public class MenuEjemplo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int opcion;

        do {
            System.out.println("=== MENÚ PRINCIPAL ===");
            System.out.println("1. Saludar");
            System.out.println("2. Calcular suma");
            System.out.println("3. Salir");
            System.out.print("Elige una opción: ");
            opcion = sc.nextInt();

            switch (opcion) {
                case 1:
                    System.out.println("¡Hola usuario!");
                    break;
                case 2:
                    System.out.print("Introduce un número: ");
                    int a = sc.nextInt();
                    System.out.print("Introduce otro número: ");
                    int b = sc.nextInt();
                    System.out.println("La suma es: " + (a + b));
                    break;
                case 3:
                    System.out.println("Saliendo del programa...");
                    break;
                default:
                    System.out.println("Opción inválida.");
            }
        } while (opcion != 3);

        sc.close();
    }
}
```



