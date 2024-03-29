# Proyecto Contador de personas - CURSO DE DEEP LEARNING IEEE
- AUTOR: Jean Carlos León Armijo
- ESTUDIANTE DE: Universidad Técnica de Ambato
- FECHA: 08/02/2024
- PAÍS/CIUDAD: ECUADOR - AMBATO

DESCRIPCIÓN COMPLETA DEL PROGRAMA:
1. Como inicio describo primero el primer script `yolov5MultiplePolygon.py` programa utiliza varias bibliotecas y módulos para contar objetos en un video y generar un nuevo video con anotaciones de las detecciones. Inicialmente, se importan las bibliotecas necesarias, como numpy, supervision, torch y argparse. Luego, se definen las rutas de entrada y salida del video. La clase CountObject se encarga de inicializar los atributos de la instancia, incluyendo la carga del modelo YOLOv5 utilizando la biblioteca Ultralytics, la creación de una paleta de colores para resaltar objetos detectados, y la definición de polígonos que delimitan las zonas de interés en el video. Se utilizan anotadores de zona y de caja para visualizar y resaltar estas regiones en el video. La función process_frame se encarga de procesar cada fotograma del video, realizando la detección de objetos, filtrando las detecciones y agregando anotaciones visuales a las zonas de interés y cajas delimitadoras. Finalmente, el método process_video inicia el proceso de procesamiento del video utilizando la función process_video de la biblioteca supervision. Cuando el script se ejecuta como un programa principal, se crea una instancia de la clase CountObject con las rutas de entrada y salida del video, y se llama al método process_video para iniciar el procesamiento del video.
2. Para despues pasar al segundo script `detector_personas_id4.py` este script utiliza diversas bibliotecas y scripts adicionales para procesar videos, realizar detección y seguimiento de objetos, y generar videos de salida con anotaciones visuales. En primer lugar, importa las bibliotecas cv2 y random, así como la clase YOLO y Annotator del módulo ultralytics.utils.plotting. Luego, importa la clase CountObject del script `yolov5MultiplePolygon.py`, que se utiliza para contar objetos en un video utilizando YOLOv5 y delimitar zonas de interés mediante polígonos. Posteriormente, se definen las rutas de entrada y salida de los videos. La clase CountObject2 utiliza el video procesado por CountObject para añadir etiquetas de identificación a los objetos detectados en cada región. En la función process_video, se abre el video de entrada y se obtiene información importante como dimensiones y FPS. Se crea un objeto cv2.VideoWriter para el video de salida. Luego, se procesa cada fotograma del video de entrada utilizando el modelo YOLOv5 para el seguimiento de objetos. Los resultados de la detección y seguimiento se añaden al video de salida, y se muestra un mensaje de progreso. Una vez procesados todos los fotogramas, se liberan los recursos y se imprime un mensaje indicando la finalización del proceso y la ubicación del video generado.
3. Por ultimo lo que se hace en el programa final que sera la interfaz grafica en el script `programa_final_detectorpersonas.py`, este script implementa una aplicación de detección de personas con una interfaz gráfica de usuario (GUI) utilizando la biblioteca Tkinter en Python. La clase DetectorPersonasApp define la estructura y funcionalidades de la interfaz. En el método __init__, se inicializa y configura la ventana principal de la interfaz con un título específico, tamaño predefinido, color de fondo y fuente predeterminada. Se añaden etiquetas de información y se insertan imágenes en la parte superior izquierda y derecha de la ventana. Luego, se crea un marco para opciones de configuración de video con botones para cargar, procesar y visualizar videos, así como un botón para salir del programa. La función cargar_video permite al usuario seleccionar un archivo de video para cargar y muestra el primer fotograma en una ventana separada. La función procesar_video ejecuta un script de detección de personas en un hilo separado, mostrando una alerta mientras se realiza el procesamiento. La función visualizar_video carga y muestra el video procesado en un lienzo dentro de la ventana principal. Además, se proporciona un botón para detener o continuar la reproducción del video. Este código también incluye un bloque condicional al final que verifica si el script se está ejecutando como un programa principal o si se está importando como un módulo en otro script. En caso de ser ejecutado como principal, se crea una instancia de la clase DetectorPersonasApp y se inicia el bucle principal de la interfaz gráfica.

## Requisitos

- Python 3.x
- PyTorch
- Numpy
- Supervision (debe estar instalado. Puede instalarlo con `pip install supervision`)
- OpenCV
- Tkinter (instalado por defecto en la mayoría de las distribuciones de Python)
- Pillow (instalado por defecto en la mayoría de las distribuciones de Python)
- PIL (Python Imaging Library)
- filedialog
- Ultralytics (yolov5)
- Tkinter
- Subprocess
- threading
- ffmpeg

## Instalación de librerias y archivos

1. Clona este repositorio:
git clone https://github.com/jeancarlosleon21/proyecto_1.git

2. Se necesitara la parte de un archivo que contiene los pesos de algunas variables descargarse de este repositorio:
https://github.com/patrick013/Object-Detection---Yolov3/blob/master/model/yolov3.weights

3. Ademas de necesitar el archivo que se descargue de:
- yolov5x6.pt en el caso de no descargarse por consola

2. Instala las dependencias:
```
pip install opencv-python
pip install git+https://github.com/ultralytics/yolov5.git
pip install numpy
pip install supervision
pip install torch torchvision torchaudio
pip install ffmpeg-python
pip install pillow
pip install tkinter
pip install ultralytics
```
- Para verificar si se tiene la libreria:
```
pip show <nombre_de_la_biblioteca>
```
- Para actualizar una libreria:
```
pip install --upgrade <nombre_de_la_biblioteca>
```


## Uso
1. Ejecute el script `detector_personas_id4.py` con los argumentos necesarios, siendo necesario tener el primer script `yolov5MultiplePolygonEl.py` ya que se importa la clase "CountObject":

```
python detector_personas_id4.py -i video_entrada.mp4 -o resultado.mp4

```

"Cabe recalcar que se debera realizar una modificación en el script, cambiandolo en la entrada y salida de los videos y ubicando las siguientes lineas"
- Codigo de python:

```
import argparse

parser = argparse.ArgumentParser(
                    prog='yolov5',
                    description='This program help to detect and count the person in the polygon region',
                    epilog='Text at the bottom of help')

parser.add_argument('-i', '--input',required=True)      # option that takes a value
parser.add_argument('-o', '--output',required=True)

args = parser.parse_args()

#alfinal del script
if __name__ == "__main__":

    obj = CountObject(args.input,args.output)
    obj.process_video()
```
2. Se podra ejecutar con un editor de codigo fuente utilizando VISUAL STUDIO CODE, tener todo en una misma carpeta los scripts se podra correr el script `programa_final_detectorpersonas.py` que incluye todo el programa completo.

   
## Explicación y funcionamiento del programa.

-RESULTADOS DEL VIDEO PROCESADO:
[![IMAGEN RESULTADOS DEL VIDEO 1](https://github.com/jeancarlosleon21/proyecto_1/blob/main/Capturas_resultados/imagen_captura1.png)]
-INTERFAZ GRAFICA REALIZADA:
[![IMAGEN RESULTADOS CON LA INTERFAZ ](https://github.com/jeancarlosleon21/proyecto_1/blob/main/Capturas_resultados/imagen_captura2.PNG)]

- Se agrega el video de explicación del codigo, asi como de los resultados obtenidos:
[VIDEO DE EXPLICACIÓN EN ONEDRIVE](https://utaedu-my.sharepoint.com/:v:/g/personal/jleon4257_uta_edu_ec/EZ-jV6BLxXxBoNOMkDKXkkMBvvkkmFokkMhN2i060239Iw?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=iZnLhm)

- Se agrega el video de los resultados obtenidos con el video pasado por el algoritmo:
[VIDEO DE RESULTADO COMPLETO](https://utaedu-my.sharepoint.com/:v:/g/personal/jleon4257_uta_edu_ec/EUXny1qnT0ZKrLHok3dQ5nsBL2RGoIUv8nk4tcrV6aKLPw?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=uvwiNl)

