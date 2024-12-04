# Proyecto-Programacion
Calcular el volumen del deslizamiento (Carretera libre colima guadalajara y minatitlan)
# volumen del deslizamiento del km39
**Autores:** Cesar Alejandro Aguirre Ramos y Flavio Cesar Juarez Rodriguez 

## Introducción
Este proyecto tiene como objetivo mitigar los deslizamientos de tierra en la carretera libre Colima-Guadalajara, una arteria vital para la conectividad y la economía de la región. Debido a las condiciones topográficas y climáticas de la zona, esta infraestructura vial es particularmente vulnerable a estos fenómenos, lo que representa un riesgo significativo tanto para la seguridad de los usuarios como para la estabilidad económica local. Además, el reciente derrumbe en Minatitlán, Colima, ha puesto de manifiesto la necesidad urgente de implementar medidas preventivas más efectivas y contar con herramientas que permitan evaluar rápidamente el impacto de estos eventos.

Con el propósito de abordar este desafío, el proyecto propone el desarrollo de modelos predictivos avanzados capaces de anticipar la ocurrencia de deslizamientos y la implementación de un programa especializado para calcular con precisión el volumen de material afectado en cada evento. Para ello, se utilizarán herramientas tecnológicas innovadoras que incluyen la recopilación y análisis de datos geoespaciales, así como metodologías avanzadas de modelado y simulación. Además, se incorporarán los datos y la experiencia obtenida en el análisis del derrumbe reciente en Minatitlán para ajustar los modelos y mejorar la precisión de las predicciones.

La combinación de estos enfoques permitirá no solo prevenir futuros incidentes, sino también optimizar las estrategias de mantenimiento vial y proponer soluciones técnicas más eficaces para la gestión de riesgos en esta infraestructura crítica. De esta manera, el proyecto no solo contribuirá a la seguridad vial, sino también a la resiliencia de la infraestructura en una región susceptible a deslizamientos de tierra.

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

#CODIGO BASE DE NUESTRO PROYECTO PARA LA CARRETERA LIBRE COLIMA-GUADALAJARA 

!apt-get install -y python3-gdal

!pip install folium

!pip install openpyxl 

from osgeo import ogr, osr

from google.colab import drive

drive.mount('/content/drive')

%cd "/content/drive/My Drive/programacion2/"

%ls

import pandas as pd

excel_path = "/content/drive/My Drive/programacion2/deslizamiento_completo.xlsx"

df = pd.read_excel(excel_path)

print(df.head())


import folium

mapa = folium.Map(location=[19.447224, -103.480806], zoom_start=10)

for index, row in df.iterrows():

    lat = row['Latitud']
    lon = row['Longitud']
    Z = row['Altura_Antes']
    # Assuming you want to display Z value in the popup:
    folium.Marker(location=[lat, lon], popup=str(Z)).add_to(mapa)
mapa

import folium

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

mapa = folium.Map(location=[19.447224, -103.4808061], zoom_start=18)

folium.Polygon(

    locations=coordenadas,
    color='blue',
    fill=True,
    fill_color='lightblue',
    fill_opacity=0.5,
    popup='Polígono'
).add_to(mapa)
mapa


pip install shapely matplotlib

import matplotlib.pyplot as plt

from shapely.geometry import Polygon

from pyproj import Proj, transform

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

wgs84 = Proj(init='epsg:4326')

utm = Proj(init='epsg:32614')  # Cambiar 32614 según tu zona UTM específica

coordenadas_utm = [(transform(wgs84, utm, lon, lat)) for lat, lon in coordenadas]

poligono = Polygon(coordenadas_utm)

area = poligono.area

print(f"El área del polígono es: {area:.2f} metros cuadrados.")

x, y = poligono.exterior.xy  # Obtener las coordenadas del contorno exterior

plt.figure(figsize=(8, 6))

plt.fill(x, y, alpha=0.5, color='lightblue', label='Polígono')

plt.plot(x, y, color='blue', linewidth=2)

plt.title("Gráfico 2D del Polígono")

plt.xlabel("Longitud (UTM)")

plt.ylabel("Latitud (UTM)")

plt.text(min(x), min(y), f'Área: {area:.2f} m²', fontsize=12, color='red', ha='left')

plt.legend()

plt.grid(True)

plt.show()

import pandas as pd

import matplotlib.pyplot as plt

from mpl_toolkits.mplot3d import Axes3D

excel_path = '/content/drive/My Drive/programacion2/deslizamiento_completo.xlsx' 

df = pd.read_excel(excel_path)

print(df.head())

latitudes = df['Latitud']

longitudes = df['Longitud']

elevaciones_antes = df['Altura_Antes']

elevaciones_despues = df['Altura_Despues']

diferencia_elevacion = elevaciones_antes - elevaciones_despues

def calcular_area_triangulo(lat1, lon1, lat2, lon2):

    """
    Calcula el área de un triángulo formado por tres puntos en el plano 2D
    utilizando la fórmula del determinante para el área de un triángulo.
    """
    return 0.5 * abs(lat1 * lon2 + lat2 * lon1)
volumen_total = 0

for i in range(1, len(df)):

    lat1, lon1 = latitudes[i-1], longitudes[i-1]
    lat2, lon2 = latitudes[i], longitudes[i]
    elev1, elev2 = elevaciones_antes[i-1], elevaciones_antes[i]
    area = calcular_area_triangulo(lat1, lon1, lat2, lon2)
    diferencia = abs(elev1 - elev2)
    volumen = area * diferencia
    volumen_total += volumen
print(f"El volumen total desplazado es: {volumen_total} unidades cúbicas")

fig = plt.figure(figsize=(10, 8))

ax = fig.add_subplot(111, projection='3d')

ax.scatter(latitudes, longitudes, elevaciones_antes, c='blue', label='Antes', marker='o')

ax.scatter(latitudes, longitudes, elevaciones_despues, c='red', label='Después', marker='^')

ax.set_xlabel('Latitud')

ax.set_ylabel('Longitud')

ax.set_zlabel('Elevación (m)')

ax.set_title('Modelo 3D de la Elevación Antes y Después del Deslizamiento')

ax.legend()

plt.show()

## CODIGO PARA LA COMPROBACION DERRUMBE MINATITLAN

!apt-get install -y python3-gdal

!pip install folium

!pip install openpyxl #para leer archivo en exel


from osgeo import ogr, osr

from google.colab import drive

drive.mount('/content/drive')

%cd "/content/drive/My Drive/programacion2/"

%ls

import pandas as pd

#Ruta del archivo Excel (sube el archivo desde tu computadora a Colab o Drive)

excel_path = "/content/drive/My Drive/programacion2/minatitlandeslizamiento_completo.xlsx"

#Leer el archivo Excel

df = pd.read_excel(excel_path)

#Mostrar las primeras filas del archivo para asegurarse de que se cargó correctamente
print(df.head())


import folium

#Crear un mapa centrado en la zona del deslizamiento

mapa = folium.Map(location=[19.390504, -103.955763], zoom_start=16)

#Añadir los puntos del archivo Excel al mapa

for index, row in df.iterrows():

    lat = row['Latitud']
    lon = row['Longitud']
    Z = row['Altura_Antes']
    # Assuming you want to display Z value in the popup:
    folium.Marker(location=[lat, lon], popup=str(Z)).add_to(mapa)
#Mostrar el mapa interactivo

mapa

import folium

#Lista de coordenadas (latitud, longitud) en orden
coordenadas = [

    [19.390504, -103.955763],
    [19.390123, -103.955442],
    [19.390579, -103.955215],
    [19.390695, -103.954644],
    [19.391532, -103.954914],
    [19.391966, -103.954829],
    [19.392472, -103.955474],
    [19.391608, -103.955515],
    [19.390664, -103.955718],
    [19.390504, -103.955763]  # Cerramos el polígono volviendo al primer punto
]

#Crear el mapa centrado en la primera coordenada

mapa = folium.Map(location=[19.390504, -103.955763], zoom_start=16)

#Añadir el polígono al mapa

folium.Polygon(

    locations=coordenadas,
    color='blue',
    fill=True,
    fill_color='lightblue',
    fill_opacity=0.5,
    popup='Polígono de deslizamiento'
).add_to(mapa)


#Mostrar el mapa interactivo
mapa

import matplotlib.pyplot as plt

from shapely.geometry import Polygon

from pyproj import CRS, Transformer

#Coordenadas del polígono (lat, lon)
coordenadas = [

    [19.390504, -103.955763],
    [19.390123, -103.955442],
    [19.390579, -103.955215],
    [19.390695, -103.954644],
    [19.391532, -103.954914],
    [19.391966, -103.954829],
    [19.392472, -103.955474],
    [19.391608, -103.955515],
    [19.390664, -103.955718],
    [19.390504, -103.955763]  # Cerramos el polígono volviendo al primer punto
]

#Definir sistemas de coordenadas

crs_wgs84 = CRS.from_epsg(4326)  # WGS84

crs_utm = CRS.from_epsg(32613)   # Cambiar según la zona UTM específica (32613 es correcto para esta región)

#Crear un transformador para convertir entre sistemas

transformer = Transformer.from_crs(crs_wgs84, crs_utm, always_xy=True)

#Convertir coordenadas (lon, lat) a (x, y) en UTM

coordenadas_utm = [transformer.transform(lon, lat) for lat, lon in coordenadas]

#Crear el polígono usando Shapely

poligono = Polygon(coordenadas_utm)

#Calcular el área del polígono en metros cuadrados

area = poligono.area

print(f"El área del polígono es: {area:.2f} metros cuadrados.")

#Crear el gráfico 2D del polígono

x, y = poligono.exterior.xy  # Obtener las coordenadas del contorno exterior

plt.figure(figsize=(8, 6))

plt.fill(x, y, alpha=0.5, color='lightblue', label='Polígono')

plt.plot(x, y, color='blue', linewidth=2)

#Añadir etiquetas y título

plt.title("Gráfico 2D del Polígono")

plt.xlabel("Coordenada Este (UTM)")

plt.ylabel("Coordenada Norte (UTM)")

#Mostrar el área en el gráfico

plt.text(min(x), min(y), f'Área: {area:.2f} m²', fontsize=12, color='red', ha='left')

#Mostrar el gráfico

plt.legend()

plt.grid(True)

plt.show()

import pandas as pd

import matplotlib.pyplot as plt

from mpl_toolkits.mplot3d import Axes3D

#Cargar el archivo Excel con las coordenadas y las elevaciones

excel_path = '/content/drive/My Drive/programacion2/minatitlandeslizamiento_completo.xlsx'  # Reemplaza con la ruta a tu archivo Excel

df = pd.read_excel(excel_path)

#Visualizar las primeras filas para asegurar que se ha cargado correctamente

print(df.head())

#Extraer las coordenadas (latitud, longitud) y las elevaciones (antes y después)

latitudes = df['Latitud']

longitudes = df['Longitud']

elevaciones_antes = df['Altura_Antes']

elevaciones_despues = df['Altura_Despues']

#Calcular la diferencia de elevación en cada punto

diferencia_elevacion = elevaciones_antes - elevaciones_despues

#Calcular el volumen de tierra movida entre puntos consecutivos

def calcular_area_triangulo(lat1, lon1, lat2, lon2):


    """
    Calcula el área de un triángulo formado por tres puntos en el plano 2D
    utilizando la fórmula del determinante para el área de un triángulo.
    """
    return 0.5 * abs(lat1 * lon2 + lat2 * lon1)

volumen_total = 0

#Iterar sobre los puntos para calcular el volumen

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

#Crear una figura 3D

fig = plt.figure(figsize=(10, 8))

ax = fig.add_subplot(111, projection='3d')

#Graficar el modelo 3D para la elevación "Antes" del deslizamiento

ax.scatter(latitudes, longitudes, elevaciones_antes, c='blue', label='Antes', marker='o')

#Graficar el modelo 3D para la elevación "Después" del deslizamiento

ax.scatter(latitudes, longitudes, elevaciones_despues, c='red', label='Después', marker='^')

#Etiquetas y título

ax.set_xlabel('Latitud')

ax.set_ylabel('Longitud')

ax.set_zlabel('Elevación (m)')

ax.set_title('Modelo 3D de la Elevación Antes y Después del Deslizamiento')

#Leyenda

ax.legend()

#Mostrar el gráfico 3D

plt.show()



## CODIGO EN COLAB CARRETERA LIBRE COLIMA-GUADALAJARA

https://colab.research.google.com/drive/1--sgT5CllInmLbbceUZYyXXcwHpTkgIU?usp=sharing
## EXEL
carretera libre colima-guadalajara

https://docs.google.com/spreadsheets/d/16ctUVfSSRQI_purXnP9oghn4KW-suEmc/edit?usp=sharing&ouid=106412577940717402382&rtpof=true&sd=true

minatitlan

https://docs.google.com/spreadsheets/d/16ctUVfSSRQI_purXnP9oghn4KW-suEmc/edit?usp=sharing&ouid=106412577940717402382&rtpof=true&sd=true

## CODIGO EN COLAB MINATITLAN

https://colab.research.google.com/drive/1Y9l803eQw7NiBlztu6pMmbfqtzGo16Z1?usp=sharing

## VIDEO EN YOUTUBE

https://youtu.be/9gDlI3mhhyw
## Resultados 
# CARRETERA LIBRE COLIMA-GUADALAJARA
El código tiene como objetivo cargar un archivo Excel desde una ubicación específica en Google Drive utilizando la librería pandas, que se usa comúnmente para manipular y analizar datos en Python. Primero, define la ruta del archivo Excel en Google Drive. Luego, utiliza la función pd.read_excel() para leer el archivo y almacenarlo en un DataFrame, que es una estructura de datos tabular en la que los datos pueden ser organizados y manipulados fácilmente. Finalmente, el código muestra las primeras cinco filas del DataFrame con df.head(), lo que permite verificar que el archivo se haya cargado correctamente y examinar brevemente su contenido antes de realizar análisis adicionales.
![image](https://github.com/user-attachments/assets/90d1b3a0-dc68-42d1-bea4-cfdd845999ab)

El código crea un mapa interactivo centrado en unas coordenadas específicas (latitud: 19.390504, longitud: -103.955763) utilizando la librería folium. Luego, recorre las filas de un archivo Excel (cargado previamente en un DataFrame) para obtener las coordenadas de latitud, longitud y la altura antes del deslizamiento. Para cada fila, agrega un marcador en el mapa con la latitud y longitud correspondientes, mostrando la altura en un mensaje emergente (popup) al hacer clic en el marcador. El resultado es un mapa con puntos interactivos que representan las ubicaciones de los deslizamientos y sus respectivas alturas.
![image](https://github.com/user-attachments/assets/92ff2ff3-02e8-40f6-9d4d-3a406527d0da)

Este código crea un mapa interactivo utilizando la librería folium, centrado en un conjunto de coordenadas específicas. Primero, define una lista de coordenadas que forman los vértices de un polígono. Luego, crea el mapa y dibuja un polígono azul con un relleno color azul claro en esas coordenadas. El mapa tiene un nivel de zoom de 16 y muestra un mensaje emergente (popup) cuando se hace clic en el polígono, indicando que se trata del "Polígono de deslizamiento". Finalmente, se muestra el mapa interactivo.

Este tipo de visualización es útil para representar áreas afectadas por deslizamientos en un mapa geográfico.
![image](https://github.com/user-attachments/assets/dc3a696f-dbe8-4ca8-aeca-bd4685cf82ae)

Este código convierte un conjunto de coordenadas geográficas (latitud, longitud) a coordenadas UTM para crear un polígono en un mapa. Utiliza las librerías Shapely para formar el polígono y calcular su área en metros cuadrados, y matplotlib para graficarlo en 2D. También incluye la visualización del área del polígono en el gráfico.

![image](https://github.com/user-attachments/assets/78d60053-17d6-4e5b-82ac-6e9eccfb326d)

Este código carga un archivo Excel con coordenadas y elevaciones de un deslizamiento. Calcula la diferencia de elevación entre puntos antes y después del deslizamiento, y usa la fórmula de área de triángulos para estimar el volumen de tierra movida. Luego, genera un gráfico 3D mostrando las elevaciones "antes" y "después" del deslizamiento y calcula el volumen total desplazado.
![image](https://github.com/user-attachments/assets/624a474a-4f34-4ab8-95ce-1ca9acf032f7)
# MINATITLAN
![image](https://github.com/user-attachments/assets/8ece2da4-18a3-4d2e-9e71-d23733df3626)

![image](https://github.com/user-attachments/assets/9963fe56-66d2-4a50-b361-190468af5b28)

![image](https://github.com/user-attachments/assets/300eb505-cacd-4760-ba0f-83be7bb0efb7)

![image](https://github.com/user-attachments/assets/d404d933-9f57-43f8-b76a-ad41885202a9)

![image](https://github.com/user-attachments/assets/bcfb4d02-adea-4583-9349-07a325dc70fc)

## capturas de pantalla
![image](https://github.com/user-attachments/assets/fe5b3aae-9a86-4b74-b505-059b9855dc40)

![image](https://github.com/user-attachments/assets/34d455fd-61ea-48e3-a4eb-60fee297797f)

![image](https://github.com/user-attachments/assets/b3b7981b-9ec9-43ef-ae85-f256bfd48feb)

![image](https://github.com/user-attachments/assets/05d9da87-6fac-4339-a8b9-f863a5bb1a0d)

![image](https://github.com/user-attachments/assets/2c93727d-68a1-43a0-a708-e478bf5db2b1)

![image](https://github.com/user-attachments/assets/7cc85a37-0a55-4703-b19f-ab4e55a3ab0c)

![image](https://github.com/user-attachments/assets/ac6358c4-6ba0-4b04-97ae-bf455cb696d1)

![image](https://github.com/user-attachments/assets/a130c123-f5cc-4ec6-a6f3-bb669db9341d)

![image](https://github.com/user-attachments/assets/6954bef5-af18-47c7-bab5-6dd33706cdc6)

![image](https://github.com/user-attachments/assets/47e39b65-8587-450b-a708-077e138f6541)




## Conclusiones
Este proyecto se desarrolló con un enfoque innovador que integró herramientas tecnológicas avanzadas y análisis geoespacial, permitiéndonos identificar los riesgos más críticos y proponer soluciones efectivas para enfrentarlos. Un aspecto destacado fue la precisión obtenida en el cálculo de variables clave, como el área y el volumen del material desplazado en deslizamientos anteriores en la carretera libre Colima-Guadalajara, así como la verificación y análisis detallado de un reciente derrumbe en Minatitlán, Colima, lo que permitió ajustar nuestras estrategias de prevención y respuesta ante futuros eventos de deslizamientos.

El uso de tecnologías como el software GIS fue fundamental, ya que permitió desarrollar un código especializado capaz de realizar estos cálculos de forma eficiente. Este programa no solo facilitó la cuantificación de las pérdidas de material, sino que también transformó la manera de abordar estos eventos, mejorando significativamente la planificación y respuesta ante deslizamientos. En el caso del derrumbe en Minatitlán, se utilizó la misma metodología para obtener las estimaciones de volumen y extensión del deslizamiento, comparando datos antes y después del evento para proporcionar una imagen precisa de su impacto.

Uno de los mayores desafíos fue integrar y adaptar múltiples códigos para lograr un programa funcional y útil en nuestras labores. Esto implicó resolver problemas técnicos relacionados con el manejo de coordenadas X, Y y Z, que son esenciales para los cálculos necesarios. A pesar de las dificultades, el trabajo en equipo y la perseverancia nos permitieron superar los obstáculos y culminar exitosamente el proyecto, logrando incluir la comprobación de los datos y la validación del volumen de material desplazado en Minatitlán.

En conclusión, este esfuerzo no solo representa un avance en la seguridad vial y la gestión de riesgos en una arteria clave para la región, sino que también evidencia cómo la tecnología y la colaboración pueden aportar soluciones innovadoras a problemas complejos, como los deslizamientos de tierra. La integración de herramientas geoespaciales y el análisis continuo de eventos, como el derrumbe en Minatitlán, son pasos fundamentales hacia una gestión más eficaz de los riesgos naturales y su mitigación.
