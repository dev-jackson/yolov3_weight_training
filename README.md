# Guia de entremaniento para yolov3

* ## Requermientos
    > Python 3.5 o superior.

    > Git ultimas versiones(recomendado).

    > Conexion estable a internet.

* ## Preparacion de datos
    * Para hacer este preceso de entrenamiento nesesitamos unos datos espeficios que requiere **yolov3** en un formato especifico de anotaciones.

* ## Formato de anotaciones
    * Nesesitamos los datos de anotaciones los cuales son las cordenadas del centro de cuadro del objeto, la altura y el ancho de dicho cuandro, y todos esto debe estar es text plano ***.txt**.
    * Los datos deben estar ordenados de la siguiente manera:

        > < object-class > <x_center> <y_center> < width > < height >

        > **Object Class:** el numero de clases en en este caso va de 0 a (n-clases)-1, en caso de que existan **100** clases entoces se diria que la ultima clase es la numero **99**.
    * Cada una de las imganes tendra su archivo de texto con el mismo nombre de la imagen y dentro de es archivo debe ir el formato anteriormente mencionado. Dado el caso de que la imagen tenga el nombre de ***ejemplo.png*** su archivo de texto seria ***ejemplo.txt***.
* ## Herramienta LabelImg
    * Esta es un herramienta de python que nos ayudara a crear las anotaciones que nesesitamos.
    * **Instalacion:**

        > pip3 install labelImg
     