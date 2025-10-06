## ¿Qué es la serialización?

La serialización es el proceso mediante el cual un objeto en memoria se transforma en una secuencia de bytes que puede guardarse en un fichero o transmitirse. Su operación inversa es la **deserialización**, que reconstruye el objeto original a partir del flujo de datos.

Para que una clase sea serializable debe:

- Implementar la interfaz `java.io.Serializable`.
    
- Tener un identificador `serialVersionUID` (recomendado).

```java
import java.io.*;

public class EscribirObjeto {
    public static void main(String[] args) {
        Persona p = new Persona("Ana", 30);

        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("datos/persona.dat"))) {
            oos.writeObject(p);
            System.out.println("Objeto serializado correctamente.");
        } catch (IOException e) {
            System.out.println("Error al escribir objeto: " + e.getMessage());
        }
    }
}

class Persona implements Serializable {
    private static final long serialVersionUID = 1L;
    private String nombre;
    private int edad;

    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }
}
```