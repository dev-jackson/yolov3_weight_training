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

        > **x_center, y_center, width, height:** las cordenadas (x,y) del centro del cuadro y el ancho y altura del mismo.
    * Cada una de las imganes tendra su archivo de texto con el mismo nombre de la imagen y dentro de es archivo debe ir el formato anteriormente mencionado. Dado el caso de que la imagen tenga el nombre de ***ejemplo.png*** su archivo de texto seria ***ejemplo.txt***.
* ## Herramienta LabelImg
    * Esta es un herramienta de python que nos ayudara a crear las anotaciones que nesesitamos.
    * **Instalacion:**

        > pip3 install labelImg
     
    * Creacion de directorio donde guardaremos nuestras imagenes y datos.

        1. Creamos una carpeta llamada ***data***(el nombre puede cambiar).
        2. Dentro de la carpeta ***data*** creamos dos carpetas mas las cuales tendras el nombre de ***images*** y ***labels***(estos nombres no pueden ser otros).
    * Dentro del directorio de  nuesta carpeta ***images*** colocaremos nuestra images del objeto.
    * Para ejecutar labelImg solo ecjecutamos el siguiente comando en el terminal:
        > labelImg
    * ### **LabelIgm**
        Esto es lo que veriamos es nuestras pantallas:

        ![Texto alternativo](/src/img/LabeImg.png "Título alternativo")
    * En este caso el espacio de trabajo saldra en black, aqui le damos clik a la opcion **Open Dir** donde eleguiremos nuestra carpeta de imagenes en esta caso **images** lo cual cargara todas las imagenes disponibles en esa carpeta.
    * ## **Donde podemos conseguir imaganes en gran catidad pata estos procesos**
        * Para esto en este caso vamos a realizar uso del navergar ***google chrome*** con la extension de ***Download All Images*** :
        ![Texto alternarnativo](/src/img/extension.png "Titulo alternativo")

        * Lo siguente solo seria hacer una busqueda en google y poner imagenes, en esta caso el objeto seria "mando" solo damos click sobre la extension y comenzara a detectar las imanges de las la pagina en la cual podemos darle un tope dando click sobre la misma.
        ![Texto alternarnativo](/src/img/GitLoad1.gif "Titulo alternativo")
        * Despues de esto se descargaria un archivo ***.zip***  dentro tenemos todas las imagenes de la paguina. Descromprimimos y pasamos esas imagenes y las colocamos en nuetra caperta ***images*** que creamos anteriormente.
        Nos quedaria asi:
        ![Texto alternarnativo](/src/img/DirImages.png "Titulo alternativo")
    * ## **Configuracion y uso labelImg**
        * Lo que aremos como primer paso es cambiar el formato de anotacion de LabelImg solo damos click en el boton que dice ***PascalVOC*** y lo cambiamos a ***Yolo***.
         ![Texto alternarnativo](/src/img/usoLabelImg.png "Titulo alternativo")
        * Una vez que hayamos echo ese cambio vamos a elegir nuestra carpeta que contenta las imagenes que hemos conseguido. Damos click en ***Open Dir***
        y buscamos nuestra carpeta deseada en esta caso ***images*** y le damos en ***Selecionar carpeta***.
        ![Texto alternarnativo](/src/img/GitLoad2.gif "Titulo alternativo")
        



    
