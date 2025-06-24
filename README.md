# Optimización de Precios y Rendimiento de Productos en Amazon

## 📊 Descripción del Proyecto

Este proyecto de análisis de datos se enfoca en comprender cómo los precios (originales y con descuento) y las calificaciones de los productos en Amazon impactan su popularidad y rendimiento. El objetivo principal es identificar patrones, descubrir insights valiosos y proporcionar recomendaciones estratégicas que puedan guiar decisiones de negocio relacionadas con precios y marketing.

Se ha construido un pipeline de datos que incluye:
-   **Limpieza y Preprocesamiento de Datos** con Python.
-   **Almacenamiento y Análisis Exploratorio (EDA)** con una base de datos SQLite.
-   **Visualización Interactiva de Datos** con Power BI Desktop.

## 🚀 Objetivos del Análisis

El análisis busca responder a las siguientes preguntas clave de negocio:

1.  **Relación entre Descuento y Popularidad (Rating Count):** ¿Los descuentos realmente impulsan la popularidad (medida por el conteo de calificaciones)? ¿Existe un "punto óptimo" de descuento que maximice la popularidad?
2.  **Impacto de la Calificación Promedio:** ¿Cómo la calificación promedio de un producto influye en su popularidad? ¿Los productos mejor calificados tienden a ser más populares?
3.  **Productos Destacados:** Identificar los productos con mejor rendimiento general (altas calificaciones y popularidad), así como aquellos que son populares con y sin descuentos específicos.
4.  **Tendencias por Categoría:** ¿Existen diferencias significativas en precios, descuentos, calificaciones y popularidad entre las distintas categorías de productos?

## 🛠️ Tecnologías y Herramientas Utilizadas

* **Python 3.x:** Lenguaje de programación principal para limpieza y orquestación de datos.
    * `pandas`: Manipulación y análisis de datos.
    * `numpy`: Soporte para operaciones numéricas.
* **Jupyter Notebook:** Entorno interactivo para el desarrollo, pruebas y documentación del análisis de datos.
* **SQLite:** Base de datos relacional ligera para el almacenamiento de datos limpios y la realización de consultas SQL complejas.
* **SQL (Standard Query Language):** Para la consulta, agregación y extracción de insights de la base de datos.
* **Power BI Desktop:** Herramienta de Business Intelligence para la creación de dashboards interactivos y visualizaciones dinámicas.
* **ODBC (Open Database Connectivity):** Para establecer la conexión entre Power BI y la base de datos SQLite.
* **Git & GitHub:** Control de versiones del código y gestión del proyecto.

## 📂 Estructura del Repositorio
```
e-commerce-sales-analysis/
├── .git/
├── .gitignore
├── README.md                                   # Este archivo
├── requirements.txt                            # Dependencias de Python
├── data/
│   ├── raw/
│   │   └── amazon.csv                          # Datos brutos originales
│   ├── cleaned/
│   │   └── cleaned_amazon_products.csv         # Datos después de la limpieza (CSV)
│   └── amazon_productos.db                     # Base de datos SQLite generada
├── notebooks/
│   ├── 01_data_cleaning.ipynb                  # Limpieza y preprocesamiento de datos
│   └── 02_sql_data_loading_and_exploration.ipynb # Carga a DB y análisis exploratorio SQL
└── dashboards/
    └── amazon_sales_dashboard.pbix             # Archivo del dashboard de Power BI

```
## 🚀 Cómo Ejecutar el Proyecto

Sigue estos pasos para replicar el análisis y explorar el dashboard:

### 1. Clonar el Repositorio

Abre tu terminal o Git Bash y ejecuta:
```bash
git clone [https://github.com/Lyll42/e-commerce-sales-analysis.git](https://github.com/Lyll42/e-commerce-sales-analysis.git)
cd e-commerce-sales-analysis
```

### 2. Configuración del Entorno Python

Se recomienda crear un entorno virtual para gestionar las dependencias.
Bash

python -m venv venv
* **En Windows:**
```bash
.\venv\Scripts\activate
```
* **En macOS/Linux:** 
```bash
source venv/bin/activate
```

Instala las librerías necesarias:
```bash

pip install -r requirements.txt
```
#
### 3. Procesamiento de Datos con Jupyter Notebooks

Inicia Jupyter Notebook o JupyterLab desde la raíz del proyecto:


jupyter notebook

Una vez en el navegador:

    Navega a la carpeta notebooks/.
    Abre y ejecuta secuencialmente todas las celdas de 01_data_cleaning.ipynb. Este notebook limpiará los datos brutos y guardará cleaned_amazon_products.csv en data/cleaned/.
    Abre y ejecuta secuencialmente todas las celdas de 02_sql_data_loading_and_exploration.ipynb. Este notebook cargará los datos limpios en amazon_productos.db (en la carpeta data/) y realizará el análisis exploratorio con consultas SQL.

### 4. Configuración para Power BI (Conexión ODBC)

**Power BI Desktop requiere un controlador ODBC para conectarse a bases de datos SQLite.**

    Instalar SQLite ODBC Driver:
        Descarga la versión adecuada (32-bit o 64-bit, según tu Power BI Desktop) desde http://ch-werner.de/sqliteodbc/.
        Ejecuta el instalador y sigue los pasos.
    Configurar una DSN de Usuario:
        Abre el "Administrador de orígenes de datos ODBC (64 bits)" (busca en Windows).
        Ve a la pestaña "DSN de usuario" y haz clic en "Agregar...".
        Selecciona "SQLite3 ODBC Driver" y haz clic en "Finalizar".
        En la ventana de configuración:
            Data Source Name: Amazon_Productos_DB (o el nombre que prefieras).
            Database Name: Haz clic en "Browse..." y selecciona el archivo amazon_productos.db que se encuentra en la carpeta data/ de tu proyecto.
        Haz clic en "OK".

### 5. Explorar el Dashboard en Power BI Desktop

    Abre Power BI Desktop.
    Ve a la carpeta dashboards/ de tu repositorio.
    Abre el archivo amazon_sales_dashboard.pbix.
    Si Power BI te pide credenciales o te muestra un error de conexión, asegúrate de que la DSN Amazon_Productos_DB esté correctamente configurada y que el archivo .db exista en la ruta especificada. Si te pide credenciales, selecciona "Anónimo" o "Predeterminado" ya que SQLite no usa usuarios/contraseñas.

## 📈 Hallazgos y Conclusiones Clave

Basado en los resultados de tu análisis, escribe tus insights más importantes aquí.

Aquí tienes algunos ejemplos de hallazgos que podrías haber encontrado (ajusta según tus datos reales):

* **Impacto de los Descuentos:** Se observó que los productos con descuentos en el rango del 61-70% tienden a acumular la mayor cantidad de rating_count promedio y total, lo que sugiere un "punto óptimo" donde los descuentos son más efectivos para impulsar la popularidad. Los productos sin descuento o con descuentos mínimos muestran una popularidad significativamente menor.
* **Influencia de la Calificación:** Existe una fuerte correlación positiva entre la calificación promedio de un producto y su popularidad. Los productos con calificaciones entre 4.0 y 4.4 (Muy Bueno) son los principales impulsores del volumen total de rating_count.
* **Productos Estrella:** Las categorías como Electrónica (especialmente auriculares y cables HDMI) dominan el ranking de productos más populares, a menudo logrando esta popularidad con descuentos significativos.
* **Productos de Demanda Intrínseca:** Se identificaron productos como [Menciona 1 o 2 ejemplos específicos del Top 10 sin descuento] que alcanzan alta popularidad sin depender de descuentos, indicando una demanda fuerte basada en su valor intrínseco o necesidad.
* **Tendencias por Categoría:** Las categorías varían ampliamente en estrategia de precios y potencial de popularidad. Por ejemplo, la categoría Electronics|Headphones,Earbuds&Accessories|Headphones muestra la mayor popularidad total a pesar de no ser la más grande por número de productos.

## 🎯 Recomendaciones de Negocio

Basado en tus hallazgos, formula recomendaciones accionables para una empresa.
* **Optimizar Estrategia de Descuentos:** Priorizar la aplicación de descuentos en el rango de 60-70% para productos seleccionados, monitoreando de cerca la respuesta en términos de popularidad y conversión.
* **Foco en la Calidad del Producto:** Invertir en mejorar la calidad y, por ende, las calificaciones promedio de los productos, ya que esto es un motor fundamental para la popularidad orgánica.
* **Análisis Categórico Continuo:** Realizar análisis detallados por categoría para adaptar las estrategias de precios y descuentos a las particularidades de cada segmento de mercado.
* **Identificar Oportunidades para Productos sin Descuento:** Promocionar los productos con alta demanda intrínseca que no necesitan descuentos, ya que representan una fuente de ingresos estable y potencialmente más rentable.

## 🔮 Futuras Mejoras

* **Integrar Datos de Ventas Reales:** Si estuvieran disponibles, integrar datos de ventas transaccionales para una correlación más precisa con los descuentos y calificaciones.
* **Análisis de Sentimiento de Reseñas:** Utilizar Procesamiento de Lenguaje Natural (NLP) para analizar el contenido de review_content y review_title y obtener insights cualitativos sobre la satisfacción del cliente.
* **Modelado Predictivo:** Desarrollar modelos de Machine Learning para predecir la popularidad o el impacto en ventas de un producto basado en su precio, descuento y calificación inicial.
* **Análisis de Competencia:** Integrar datos de la competencia para comparar estrategias de precios y rendimiento.

## Preview
[![unknown-2025-06-24-17-48.png](https://i.postimg.cc/9fCdY4vM/unknown-2025-06-24-17-48.png)](https://postimg.cc/9DgwWfX5)

<!-- end list -->