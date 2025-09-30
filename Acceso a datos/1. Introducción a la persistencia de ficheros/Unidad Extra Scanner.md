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
![[Pasted image 20250930122326.png]]

## Leer archivos con Scanner
```java
import java.io.File;
import java.util.Scanner;

public class LeerArchivoScanner {
    public static void main(String[] args) {
        try {
            File archivo = new File("datos/entrada.txt");
            Scanner sc = new Scanner(archivo);

            while (sc.hasNextLine()) {
                String linea = sc.nextLine();
                System.out.println("Línea: " + linea);
            }

            sc.close();
        } catch (Exception e) {
            System.out.println("Error al leer archivo: " + e.getMessage());
        }
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

![[Pasted image 20250930122634.png]]


##  Comparación con otras clases de entrada

| Clase            | Ventajas                                | Inconvenientes                      |
| ---------------- | --------------------------------------- | ----------------------------------- |
| `Scanner`        | Fácil de usar, soporta tipos primitivos | Más lento que `BufferedReader`      |
| `BufferedReader` | Muy eficiente en lectura de texto       | Necesita conversión manual de tipos |
| `FileReader`     | Lectura directa de archivos             | Requiere envoltorios (buffers)      |
## Buenas prácticas 
- Cerrar siempre con `sc.close()` para liberar recursos.
    
- Si se usan métodos mixtos (`nextInt` y `nextLine`), limpiar el buffer.
    
- Para proyectos grandes, combinarlo con **clases POJO** para estructurar datos.
    
- Evitar su uso en **aplicaciones con ficheros enormes**, donde `BufferedReader` es más eficiente.