# WALMART-SQL-PYTHON-PROYECT
DIAGRAMA DE FLUJO:
<img width="1920" height="1080" alt="PROCESS DATA CLEAN DATA" src="https://github.com/user-attachments/assets/d32441fc-479a-4897-af57-04f0e13cbbc8" />
Este proyecto es una solución completa de análisis de datos diseñada para extraer insights clave del negocio a partir de los datos de ventas de Walmart. Utilizamos Python para el procesamiento y análisis de datos, SQL para consultas avanzadas, y técnicas estructuradas para resolver preguntas críticas de negocio. El proyecto es ideal para analistas de datos que buscan desarrollar habilidades en manipulación de datos, consultas SQL y creación de pipelines de datos.

Pasos del Proyecto
1. Configurar el Entorno
- Herramientas usadas: Visual Studio Code (VS Code), Python, SQL (MySQL y PostgreSQL)
- Objetivo: Crear un espacio de trabajo organizado en VS Code y estructurar carpetas para facilitar el desarrollo y manejo de datos.

2. Configurar la API de Kaggle
- Obtén tu token de API en tu perfil de Kaggle descargando el archivo JSON.
- Coloca el archivo kaggle.json en la carpeta local .kaggle.
- Usa el comando kaggle datasets download -d <ruta-del-dataset> para descargar los datos directamente en tu proyecto.

3. Descargar Datos de Ventas de Walmart
Fuente de datos: Usa la API de Kaggle para descargar los datasets de ventas de Walmart.
Enlace del dataset: Walmart Sales Dataset (Reemplaza con el link real)
Almacenamiento: Guarda los datos en la carpeta data/ para fácil acceso.

4. Instalar Librerías Necesarias y Cargar Datos
Librerías:

bash
Copiar
Editar
pip install pandas numpy sqlalchemy mysql-connector-python psycopg2
- Carga de datos: Lee los datos en un DataFrame de Pandas para análisis inicial y transformaciones.

5. Explorar los Datos
Objetivo: Realizar una exploración inicial para entender la distribución, nombres de columnas, tipos y posibles problemas.
Análisis: Usa funciones como .info(), .describe() y .head() para obtener una visión rápida.

6. Limpieza de Datos
Eliminar duplicados: Identifica y elimina registros duplicados.
Manejo de valores faltantes: Elimina o rellena datos faltantes según sea necesario.
Corrección de tipos: Asegura que todas las columnas tengan tipos de datos correctos (fechas, números, etc.).
Formateo de moneda: Usa .replace() para limpiar símbolos de moneda.
Validación: Verifica la consistencia después de limpiar.

<pre> ```import pandas as pd

df = pd.read_csv(r'C:\Users\alons\Desktop\Proyect-walmart\Walmart.csv', encoding_errors='ignore')

print(df.head())

print("Duplicados:", df.duplicated().sum())
print("Nulos por columna:\n", df.isnull().sum())

df.dropna(inplace=True)

print("Nulos después de dropna:\n", df.isnull().sum())
print("Forma del DataFrame:", df.shape)
print("Tipos de datos:\n", df.dtypes)

df['unit_price'] = df['unit_price'].str.replace('$', '', regex=False)

print(df.head())

df['unit_price'] = pd.to_numeric(df['unit_price'], errors='coerce')

df['total'] = df['unit_price'] * df['quantity']

print(df.head())

df.to_csv(r'C:\Users\alons\Desktop\Proyect-walmart\datos_limpios.csv', index=False)

print(" Archivo limpio guardado como 'datos_limpios.csv'")``` </pre>


8. Ingeniería de Características
Crear nuevas columnas: Calcula el monto total por transacción multiplicando unit_price por quantity.
Mejorar dataset: Facilita análisis y agregaciones posteriores con SQL.

9. Cargar Datos a MySQL y PostgreSQL
Configurar conexiones: Usa SQLAlchemy para conectar y cargar datos limpios a MySQL y PostgreSQL.
Creación de tablas: Automatiza creación de tablas e inserción con scripts Python.
Verificación: Ejecuta consultas para asegurar que los datos se cargaron correctamente.

10. Análisis SQL: Consultas Complejas y Resolución de Problemas de Negocio
Analiza tendencias de ingresos por sucursal y categoría.
Identifica las categorías de productos más vendidas.
Evalúa el rendimiento de ventas por tiempo, ciudad y método de pago.
Detecta períodos pico de ventas y patrones de compra.
Analiza márgenes de ganancia por sucursal y categoría.
Documenta objetivo, método y resultados de cada consulta.
