# ⚔️ Comparativa de Rendimiento: JSF en ide vs Spring Boot en Docker

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

- ## 📈 Gráficas comparativas

### 100 hilos

![Comparativa 100 hilos](comparativa_100.png)

### 1000 hilos

![Comparativa 1000 hilos](comparativa_1000.png)

## 🔌 Conexión a la Base de Datos

Las explicaciones sobre cómo realizar la conexión de JSF a MySQL y de Spring Boot a PostgreSQL están disponibles en los siguientes archivos de texto:

- [Conexion JSF a MySQL](docs/conexion_jsf_mysql.txt)
- [Conexion Spring Boot a PostgreSQL](docs/conexion_spring_postgresql.txt)

## ✅ Conclusión

Spring Boot muestra una mejor escalabilidad y eficiencia bajo carga alta, con menor consumo de recursos y mayor rendimiento por segundo.

---


🙌 Gracias por visitar este repositorio. ¡Cualquier feedback o estrella es bienvenida!

