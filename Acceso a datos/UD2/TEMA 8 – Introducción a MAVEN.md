## TEMA 8.1 – Maven: Gestión de dependencias y automatización de proyectos Java

## Descripción

Este tema introduce **Apache Maven**, la herramienta más utilizada en el ecosistema Java para **gestionar dependencias**, **construir proyectos** y **automatizar el ciclo de vida del software**. Permite que un equipo de desarrollo trabaje con proyectos Java organizados, reproducibles y compatibles con cualquier entorno.

## Introducción

Maven es una herramienta de **construcción y gestión de proyectos (Build Tool)**. Nació para resolver un problema muy común: que cada proyecto Java tenía su propia estructura, sus librerías dispersas y dependencias difíciles de mantener.

Con Maven:

- El proyecto sigue una estructura estándar (`src/main/java`, `src/test/java`, etc.).
    
- Las librerías externas se descargan automáticamente.
    
- Se pueden generar ejecutables, documentaciones, informes y empaquetados.
    

## 1. Conceptos clave

|Concepto|Descripción|
|---|---|
|**Proyecto Maven**|Un conjunto de archivos con estructura predefinida y un archivo central llamado `pom.xml`.|
|**POM** _(Project Object Model)_|Archivo XML principal del proyecto (`pom.xml`) donde se definen el nombre, versión, dependencias, plugins y configuración.|
|**Repositorio Maven**|Lugar donde se almacenan las dependencias (librerías `.jar`). Puede ser local o remoto.|
|**Dependencia**|Librería externa que el proyecto necesita (por ejemplo, el conector JDBC de MySQL).|
|**Plugin**|Herramienta que amplía las capacidades de Maven (por ejemplo, empaquetar en `.jar`, ejecutar pruebas o generar documentación).|

## 2. Estructura estándar de un proyecto Maven

MiProyecto/
│
├── pom.xml
└── src/
    ├── main/
    │   ├── java/        ← Código fuente principal
    │   └── resources/   ← Archivos de configuración
    └── test/
        └── java/        ← Pruebas unitarias (opcional)

Esta estructura la detecta automáticamente **IntelliJ IDEA**, **VS Code**, **Eclipse**, y **Jupyter Lab con kernel Java (11)**.

## 3. El archivo `pom.xml`

El archivo `pom.xml` es el corazón del proyecto Maven. Ejemplo mínimo de un proyecto Java 11:

<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.campusfp</groupId>
  <artifactId>EjemploMaven</artifactId>
  <version>1.0-SNAPSHOT</version>

  <dependencies>
    <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-j</artifactId>
      <version>9.0.0</version>
    </dependency>
  </dependencies>
</project>

## 4. Tipos de repositorios Maven

|Tipo|Ubicación|Descripción|
|---|---|---|
|**Local**|`C:\Users\<usuario>\.m2\repository`|Carpeta en tu equipo donde Maven guarda las librerías descargadas.|
|**Central (Remote)**|[https://repo.maven.apache.org/maven2/](https://repo.maven.apache.org/maven2/)|Repositorio oficial donde Maven busca dependencias públicas.|
|**Privado (Corporate)**|En servidores de empresa|Repositorios internos de organizaciones con dependencias propias.|

## 5. Comandos básicos de Maven

Los comandos se ejecutan en la consola o desde IntelliJ IDEA → pestaña “Maven”.

|Comando|Descripción|
|---|---|
|`mvn clean`|Limpia el proyecto (borra `target/`).|
|`mvn compile`|Compila el código fuente.|
|`mvn package`|Empaqueta el proyecto (en `.jar` o `.war`).|
|`mvn install`|Instala el `.jar` en el repositorio local (`.m2`).|
|`mvn dependency:tree`|Muestra todas las dependencias y versiones.|

## 6. Crear un proyecto Maven en IntelliJ IDEA

1. **Archivo → Nuevo Proyecto → Maven**
    
2. Selecciona el **SDK de Java (JDK 17 o superior)**
    
3. Escribe:
    
    - _Group Id:_ `com.campusfp.dam`
        
    - _Artifact Id:_ `ProyectoAccesoDatos`
        
4. IntelliJ genera la estructura estándar con `pom.xml`.
    
5. Abre el panel lateral “Maven” → **Reload Project**.
    

Consejo docente: haz que cada alumno cree su propio proyecto Maven antes de empezar JDBC, así comprenderán el porqué de los `pom.xml` en clase.

## 7. Actualizar dependencias

Cuando cambias el `pom.xml`, Maven **no descarga automáticamente** las nuevas librerías hasta que:

- En IntelliJ: clic derecho → _Maven → Reload Project_, o
    
- En consola: `mvn clean install`.
    

Cada dependencia nueva se descargará en tu `.m2` local.

## 8. Añadir dependencias

Para agregar librerías externas, busca el _Group Id_, _Artifact Id_ y _Version_ en el **repositorio central**:

👉 [https://mvnrepository.com/](https://mvnrepository.com/)

Por ejemplo, para añadir **HikariCP**:

<dependency>
  <groupId>com.zaxxer</groupId>
  <artifactId>HikariCP</artifactId>
  <version>5.1.0</version>
</dependency>

## 9. Enlaces de interés

|Tema|Recurso|
|---|---|
|Documentación oficial|[https://maven.apache.org/](https://maven.apache.org/)|
|Repositorio de dependencias|[https://mvnrepository.com/](https://mvnrepository.com/)|
|Tutorial de inicio rápido|[https://maven.apache.org/guides/getting-started/](https://maven.apache.org/guides/getting-started/)|
|Curso oficial Apache Maven|[https://www.baeldung.com/maven](https://www.baeldung.com/maven)|
|Configuración IntelliJ + Maven|[https://www.jetbrains.com/help/idea/maven-support.html](https://www.jetbrains.com/help/idea/maven-support.html)|

## 10. Resumen final

|Concepto|Maven|Sin Maven|
|---|---|---|
|Gestión de dependencias|Automática desde repositorios|Manual (copiar `.jar`)|
|Estructura del proyecto|Estándar y portable|Variable y difícil de mantener|
|Compilación|Comando único `mvn package`|Compilación manual en IDE|
|Portabilidad|Total entre equipos|Limitada|
|Aprendizaje|Ideal para proyectos reales DAM|No recomendable en entornos profesionales|

**Conclusión:** Maven no es solo una herramienta de construcción, sino la base del ecosistema Java moderno. Usarla desde el principio permite a los alumnos entender la importancia de la automatización, la reproducibilidad y la gestión de dependencias.