# ⚔️ Comparativa de Rendimiento: JSF vs Spring Boot en Clúster

Este repositorio contiene los resultados y configuraciones utilizadas para evaluar el rendimiento de una arquitectura Monolítica (JSF) frente a una arquitectura de Microservicios (Spring Boot) bajo diferentes cargas concurrentes (100 y 1000 hilos).

🔗 Ver presentación visual: [Google Site del Proyecto](https://sites.google.com/view/jsfspring/inicio)

## 📌 Objetivo

Analizar la escalabilidad y eficiencia entre JSF y Spring Boot en un entorno clúster, mediante pruebas de estrés con JMeter.

## 🔧 Estructura

- `pruebas/jmeter/`: Archivos `.jmx` para JMeter.
- `pruebas/resultados/`: Archivos `.csv` con los resultados brutos.
- `charts/`: Scripts en JavaScript para visualizar resultados con Chart.js.
- `docs/`: Documentación adicional y análisis de resultados.
- `screenshots/`: Capturas de gráficas comparativas.

## 🧪 Pruebas realizadas

| Hilos | JSF (req/s) | Spring Boot (req/s) |
|-------|-------------|---------------------|
| 100   | 44          | 101                 |
| 1000  | 37          | 462                 |

## 📊 Recursos usados

- Apache JMeter
- Chart.js + ChartDataLabels
- HTML + CSS básico
- Google Sites (para presentación visual)

## ✅ Conclusión

Spring Boot muestra una mejor escalabilidad y eficiencia bajo carga alta, con menor consumo de recursos y mayor rendimiento por segundo.

---

## 🔌 Conexión a la Base de Datos

### Conexión a la base de datos en **JSF** con **MySQL**

La aplicación JSF utiliza una clase estática para establecer la conexión con la base de datos MySQL. La clase `ConexionBD.java` maneja las conexiones utilizando los parámetros configurados en un archivo `web.xml` (o puedes configurarlo directamente en la clase).

#### **Clase de conexión (JSF)**

```java
public class ConexionBD {
    private static Connection conn;

    public static Connection getConnection() {
        if (conn == null) {
            try {
                String url = "jdbc:mysql://localhost:3306/mi_base_de_datos";
                String user = "root";
                String password = "tu_contraseña";
                conn = DriverManager.getConnection(url, user, password);
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        return conn;
    }
}
Configuración en web.xml (opcional)
xml
Copiar
Editar
<servlet>
    <servlet-name>facesServlet</servlet-name>
    <servlet-class>javax.faces.webapp.FacesServlet</servlet-class>
    <init-param>
        <param-name>javax.faces.PROJECT_STAGE</param-name>
        <param-value>Production</param-value>
    </init-param>
</servlet>

<servlet-mapping>
    <servlet-name>facesServlet</servlet-name>
    <url-pattern>*.xhtml</url-pattern>
</servlet-mapping>
Base de datos: MySQL.

Driver JDBC: mysql-connector-java (asegúrate de tenerlo en las dependencias de tu pom.xml o lib).

URL de conexión: Configurada en la clase de conexión.

Conexión a la base de datos en Spring Boot con PostgreSQL
Spring Boot utiliza Spring Data JPA para gestionar la conexión con la base de datos PostgreSQL a través de Hibernate. En el archivo application.properties se configura la conexión con la base de datos.

Configuración en application.properties
properties
Copiar
Editar
spring.datasource.url=jdbc:postgresql://localhost:5432/mi_base_de_datos
spring.datasource.username=usuario
spring.datasource.password=tu_contraseña
spring.datasource.driver-class-name=org.postgresql.Driver
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
Entidad JPA (Spring Boot)
java
Copiar
Editar
@Entity
public class Producto {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String nombre;
    private Double precio;

    // Getters y setters
}
Base de datos: PostgreSQL.

ORM: Hibernate/JPA.

Dependencias: Asegúrate de tener spring-boot-starter-data-jpa y postgresql en tu pom.xml.

xml
Copiar
Editar
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
</dependency>
📝 Notas adicionales
Si prefieres trabajar con Docker para ambos proyectos, puedes configurar contenedores separados para JSF con MySQL y Spring Boot con PostgreSQL. Los archivos necesarios están incluidos en la carpeta docker/ para Spring Boot, y puedes seguir una estructura similar para JSF.

markdown
Copiar
Editar

### Pasos para subirlo a GitHub

1. **Asegúrate de tener el archivo `README.md` actualizado con la nueva información.**
2. **Sube los cambios al repositorio:**
   Si ya tienes el repositorio configurado y conectado, solo tienes que agregar, hacer commit y subir los cambios:

   ```bash
   git add README.md
   git commit -m "Agregada documentación sobre conexiones a bases de datos en JSF y Spring Boot"
   git push origin master
Con estos pasos, tu repositorio tendrá toda la documentación necesaria para que otros puedan entender cómo conectar los proyectos con las bases de datos MySQL y PostgreSQL.

---

🙌 Gracias por visitar este repositorio. ¡Cualquier feedback o estrella es bienvenida!

