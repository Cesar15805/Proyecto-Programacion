# Proyecto-Programacion
Calcular el volumen del deslizamiento de la carretera libre COL-GDL km 39
Código markdown
# volumen del deslizamiento del km39
**Autores:** Cesar Alejandro Aguirre Ramos y Flavio Cesar Juarez Rodriguez 

## Introducción
Este proyecto tiene como objetivo mitigar los deslizamientos de tierra en la carretera libre Colima-Guadalajara, una arteria vital para la conectividad y la economía de la región. Debido a las condiciones topográficas y climáticas de la zona, esta infraestructura vial es particularmente vulnerable a estos fenómenos, lo que representa un riesgo significativo tanto para la seguridad de los usuarios como para la estabilidad económica local.

Con el propósito de abordar este desafío, el proyecto propone el desarrollo de modelos predictivos avanzados capaces de anticipar la ocurrencia de deslizamientos y la implementación de un programa especializado para calcular con precisión el volumen de material afectado en cada evento. Para ello, se utilizarán herramientas tecnológicas innovadoras que incluyen la recopilación y análisis de datos geoespaciales, así como metodologías avanzadas de modelado y simulación.

La combinación de estos enfoques permitirá no solo prevenir futuros incidentes, sino también optimizar las estrategias de mantenimiento vial y proponer soluciones técnicas más eficaces para la gestión de riesgos en esta infraestructura crítica.

## Desarrollo
Cálculo del Volumen de un Deslizamiento de Tierra
Para calcular el volumen de un deslizamiento de tierra, se pueden seguir los pasos que se describen a continuación. Este enfoque se basa en mediciones del terreno afectado y utiliza principios geomorfológicos y geotécnicos.

1. Recolección de Datos del Terreno
Perfiles del terreno antes y después del deslizamiento: Se obtienen mediante levantamientos topográficos, drones con tecnología LiDAR, imágenes satelitales o mapas de elevación digital (DEM).
Delimitación del área del deslizamiento: Se realiza utilizando herramientas como Sistemas de Información Geográfica (SIG) o mediante observaciones en campo para trazar el perímetro del área afectada.
2. Identificación de Variables Clave
Área del deslizamiento (A): Es la extensión horizontal de la zona afectada, medida en metros cuadrados (𝑚2).
Espesor promedio del deslizamiento (t): Representa la profundidad promedio del material deslizado, obtenida como la diferencia entre la superficie original y el nivel actual del terreno, medida en metros (𝑚).
3. Fórmula para el Cálculo del Volumen
El volumen del deslizamiento (V) se calcula utilizando la fórmula básica:
V=A×t
Donde:
V: Volumen del material deslizado (𝑚3).
A: Área del deslizamiento (m2).
t: Espesor promedio del deslizamiento (m).
Herramientas Sugeridas
Topografía: Estaciones totales, GPS de precisión.
Análisis geoespacial: SIG (ArcGIS, QGIS).
Modelado avanzado: GeoStudio, Slide2.
Drones: Con tecnología LiDAR para captar detalles precisos de la superficie afectada.

## Manejo de Datos
Análisis de Datos: Cálculo del Volumen de un Deslizamiento de Tierra
El cálculo del volumen de un deslizamiento de tierra implica la recolección, procesamiento y análisis de datos topográficos y geomorfológicos. Este análisis permite estimar la cantidad de material desplazado, lo cual es esencial para evaluar impactos geológicos, planificar medidas de mitigación y diseñar soluciones de ingeniería. A continuación, se presentan los pasos detallados del análisis:

1. Recolección de Datos del Terreno
Para una estimación precisa del volumen, se requiere información sobre la superficie antes y después del deslizamiento.
Técnicas utilizadas:
Levantamientos topográficos: Estaciones totales o GPS de alta precisión.
Imágenes satelitales o DEMs (Modelos de Elevación Digital): Análisis a gran escala del área afectada.
Delimitación del área:
Se define el perímetro del deslizamiento mediante observación de campo o herramientas SIG como ArcGIS o QGIS. La precisión en esta etapa es crucial para el cálculo del área.
2. Identificación de Variables Clave
Área del deslizamiento (A): Se mide en metros cuadrados (𝑚2), representando la extensión horizontal de la zona afectada.
Espesor promedio del deslizamiento (t): Calculado como la diferencia promedio entre las superficies antes y después del deslizamiento, expresado en metros (𝑚). Este valor se obtiene con técnicas de interpolación entre ambos perfiles.
3. Cálculo del Volumen (V)
El volumen del material deslizado se calcula mediante la fórmula:
V=A×t
Donde:
V: Volumen del deslizamiento (𝑚3)
A: Área del deslizamiento (𝑚2)
𝑡: Espesor promedio (𝑚)
4. Herramientas Sugeridas
Topografía:
Estaciones totales y GPS de precisión para levantamientos detallados.
Análisis geoespacial:
Software como ArcGIS o QGIS para analizar mapas y delimitar áreas.
Captura de datos precisos para áreas de difícil acceso.
Consideraciones Finales
El análisis depende de la calidad de los datos iniciales. Factores como la heterogeneidad del terreno, la compactación del material deslizado y la precisión de las mediciones pueden influir en los resultados. La integración de tecnologías avanzadas como LiDAR y SIG mejora significativamente la exactitud del cálculo y facilita la planificación de medidas correctivas.

Este enfoque sistemático ofrece una base sólida para estudios geotécnicos y proyectos de mitigación de desastres.

CODIGO BASE DE NUESTRO PROYECTO

!apt-get install -y python3-gdal
!pip install folium
!pip install openpyxl #para leer archivo en exel

from osgeo import ogr, osr
from google.colab import drive
drive.mount('/content/drive')
%cd "/content/drive/My Drive/programacion2/"
%ls

import pandas as pd
# Ruta del archivo Excel (sube el archivo desde tu computadora a Colab o Drive)
excel_path = "/content/drive/My Drive/programacion2/deslizamiento_completo.xlsx"
# Leer el archivo Excel
df = pd.read_excel(excel_path)
# Mostrar las primeras filas del archivo para asegurarse de que se cargó correctamente
print(df.head())

import folium
# Crear un mapa centrado en la zona del deslizamiento
mapa = folium.Map(location=[19.447224, -103.480806], zoom_start=10)
# Añadir los puntos del archivo Excel al mapa
for index, row in df.iterrows():
    lat = row['Latitud']
    lon = row['Longitud']
    Z = row['Altura_Antes']
    # Assuming you want to display Z value in the popup:
    folium.Marker(location=[lat, lon], popup=str(Z)).add_to(mapa)
# Mostrar el mapa interactivo
mapa

import folium
# Lista de coordenadas (latitud, longitud)
coordenadas = [
    [19.447288, -103.480412],
    [19.447440, -103.480445],
    [19.447542, -103.480485],
    [19.447690, -103.480859],
    [19.447569, -103.481000],
    [19.447545, -103.481161],
    [19.447224, -103.480806],
    [19.447288, -103.480412]  # Cerramos el polígono volviendo al primer punto
]
# Crear el mapa centrado en la primera coordenada
mapa = folium.Map(location=[19.447224, -103.4808061], zoom_start=18)
# Añadir el polígono al mapa
folium.Polygon(
    locations=coordenadas,
    color='blue',
    fill=True,
    fill_color='lightblue',
    fill_opacity=0.5,
    popup='Polígono'
).add_to(mapa)
# Mostrar el mapa interactivo
mapa


pip install shapely matplotlib
import matplotlib.pyplot as plt
from shapely.geometry import Polygon
from pyproj import Proj, transform
# Coordenadas del polígono (lat, lon)
coordenadas = [
    [19.447288, -103.480412],
    [19.447440, -103.480445],
    [19.447542, -103.480485],
    [19.447690, -103.480859],
    [19.447569, -103.481000],
    [19.447545, -103.481161],
    [19.447224, -103.480806],
    [19.447288, -103.480412]
]
# Proyección geográfica (WGS84)
wgs84 = Proj(init='epsg:4326')
# Proyección UTM (usando un sistema de coordenadas para la región)
utm = Proj(init='epsg:32614')  # Cambiar 32614 según tu zona UTM específica
# Convertir las coordenadas (lat, lon) a UTM (x, y)
coordenadas_utm = [(transform(wgs84, utm, lon, lat)) for lat, lon in coordenadas]
# Crear el polígono usando Shapely
poligono = Polygon(coordenadas_utm)
# Calcular el área del polígono en metros cuadrados
area = poligono.area
print(f"El área del polígono es: {area:.2f} metros cuadrados.")
# Crear el gráfico 2D del polígono
x, y = poligono.exterior.xy  # Obtener las coordenadas del contorno exterior
plt.figure(figsize=(8, 6))
plt.fill(x, y, alpha=0.5, color='lightblue', label='Polígono')
plt.plot(x, y, color='blue', linewidth=2)
# Añadir etiquetas y título
plt.title("Gráfico 2D del Polígono")
plt.xlabel("Longitud (UTM)")
plt.ylabel("Latitud (UTM)")
# Mostrar el área en el gráfico
plt.text(min(x), min(y), f'Área: {area:.2f} m²', fontsize=12, color='red', ha='left')
# Mostrar el gráfico
plt.legend()
plt.grid(True)
plt.show()

import pandas as pd
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
#Cargar el archivo Excel con las coordenadas y las elevaciones
excel_path = '/content/drive/My Drive/programacion2/deslizamiento_completo.xlsx'  # Reemplaza con la ruta a tu archivo Excel
df = pd.read_excel(excel_path)
# Visualizar las primeras filas para asegurar que se ha cargado correctamente
print(df.head())
# Extraer las coordenadas (latitud, longitud) y las elevaciones (antes y después)
latitudes = df['Latitud']
longitudes = df['Longitud']
elevaciones_antes = df['Altura_Antes']
elevaciones_despues = df['Altura_Despues']
# Calcular la diferencia de elevación en cada punto
diferencia_elevacion = elevaciones_antes - elevaciones_despues
# Calcular el volumen de tierra movida entre puntos consecutivos
def calcular_area_triangulo(lat1, lon1, lat2, lon2):
    """
    Calcula el área de un triángulo formado por tres puntos en el plano 2D
    utilizando la fórmula del determinante para el área de un triángulo.
    """
    return 0.5 * abs(lat1 * lon2 + lat2 * lon1)
volumen_total = 0
# Iterar sobre los puntos para calcular el volumen
for i in range(1, len(df)):
    lat1, lon1 = latitudes[i-1], longitudes[i-1]
    lat2, lon2 = latitudes[i], longitudes[i]
    elev1, elev2 = elevaciones_antes[i-1], elevaciones_antes[i]
    # Calcular el área del triángulo formado por los puntos consecutivos
    area = calcular_area_triangulo(lat1, lon1, lat2, lon2)
    # Calcular la diferencia de elevación
    diferencia = abs(elev1 - elev2)
    # Calcular el volumen aproximado (Área * Diferencia de elevación)
    volumen = area * diferencia
    # Sumar al volumen total
    volumen_total += volumen
print(f"El volumen total desplazado es: {volumen_total} unidades cúbicas")
# Crear una figura 3D
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection='3d')
# Graficar el modelo 3D para la elevación "Antes" del deslizamiento
ax.scatter(latitudes, longitudes, elevaciones_antes, c='blue', label='Antes', marker='o')
# Graficar el modelo 3D para la elevación "Después" del deslizamiento
ax.scatter(latitudes, longitudes, elevaciones_despues, c='red', label='Después', marker='^')
# Etiquetas y título
ax.set_xlabel('Latitud')
ax.set_ylabel('Longitud')
ax.set_zlabel('Elevación (m)')
ax.set_title('Modelo 3D de la Elevación Antes y Después del Deslizamiento')
# Leyenda
ax.legend()
# Mostrar el gráfico 3D
plt.show()

## Resultados
![image](https://github.com/user-attachments/assets/90d1b3a0-dc68-42d1-bea4-cfdd845999ab)


## Conclusiones
Conclusiones del proyecto y posibles mejoras futuras.
