#  Análisis de Casos de Dengue por Región

Este proyecto permite consultar, visualizar y exportar datos ficticios de casos de Dengue agrupados por región utilizando **SQL** y **Python**.

---

##  Requisitos

- Python 3.x  
- Pandas  
- Matplotlib  
- Conexión a una base de datos con la tabla `Casos_Dengue`  
  (debe incluir las columnas `region` y `casos`)

---

##  1. Consulta SQL

Se agrupan los casos de Dengue por región usando una consulta SQL:

```python
import pandas as pd

query = '''
--  SQL: Sumar casos por región
SELECT region, SUM(casos) AS total_casos
FROM Casos_Dengue
GROUP BY region
'''

df = pd.read_sql_query(query, conn)
Descripción :
Esta consulta suma los casos agrupándolos por región y los carga en un DataFrame de Pandas.

 2. Visualización de los Datos
Se genera un gráfico de barras para representar visualmente los casos por región:


import matplotlib.pyplot as plt

plt.figure(figsize=(8,5))
plt.bar(df['region'], df['total_casos'], color='salmon')
plt.title('Casos de Dengue por Región')
plt.xlabel('Región')
plt.ylabel('Total de Casos')
plt.grid(True, axis='y', linestyle='--', alpha=0.6)
plt.tight_layout()
plt.show()
Descripción :
Se utiliza matplotlibpara graficar los datos en forma de barras. Cada barra representa una región y el total de casos reportados en ella.

 3. Exportación de Resultados
Los datos y el gráfico se guardan para su posterior análisis o presentación:


df.to_csv("resumen_dengue.csv", index=False)
plt.savefig("grafico_dengue.png")
resumen_dengue.csv : archivo con los datos agrupados por región.

grafico_dengue.png : imagen del gráfico de barras generadas.


 Créditos
Este proyecto fue creado como una práctica de integración entre consultas SQL, análisis con Pandas y visualización con Matplotlib.


