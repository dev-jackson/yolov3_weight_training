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
        * Con el directorio ya selecionado lo que veremos es nuestra primera imagen que se encuentra en la caarpeta y lo que sigue es crear nuestro Box delimitador indicando donde esta el objeto el cuando queremos hacer el entrenamiento.
            1. Damos click en ***Create\nReactBox***
            2. con el mouse arastramos donde esta el objeto requerido.
            3. Una vez echo el box saldra u ventana donde ingresaremos el nombre del ***lable*** en este cado ***joystick***.
            ![Texto alternarnativo](/src/img/GitLoad3.gif  "Titulo alternativo")
        * En el caso de que tengasmo mas de uno del mismo obejto en la misma images tambien lo delimitamos y le damos el mismo nombre de label. Una vez puesto el label al primer obejtos saldra en una lista para elejir.
        ![Texto alternarnativo](/src/img/usoLabelImg1.png "Titulo alternativo")
        * Depues de hacer esto hacemos clik en el boton guardar y guardamos el achivo ***.txt*** en la misma carpeta de las imagenes ***images*** 
        *  Despues de guardar el ***txt*** con el mismo nombre de la la imgen donde se hizo el proceso, damos clink en ***Next Image***
        ![Texto alternarnativo](/src/img/GitLoad4.gif  "Titulo alternativo")
        * **Este proceso lo repetiremos con todas la imagenes dentro de la carpeta, es tedioso pero esta es la manera para entrenar un objeto customizado**
        * Despues de ese proceso deberia quedar su caperta de images de las siguiente manera:
        ![Texto alternarnativo](/src/img/dirImages2.png  "Titulo alternativo")
* ## **Obtencion de un modelo entreand(Darknet)**
    * Para obtener este modelo pre-entrenado para la usar en nuetro proyecto hacemos un ***git clone*** y entramos en el directorio descargado:
        ``` PowerShell
        git clone https://github.com/AlexeyAB/darknet.git
        cd darknet
        ```
    * Si tiene una máquina basada en ***NVIDIA GPU*** e instaló CUDA, haga ***GPU = 1*** en el Makefile. También puede compilarlo con OpenCV haciendo ***OPENCV = 1*** en el Makefile, pero asegúrese de tener OpenCV instalado (OpenCV para C / C ++ no para Python).
    * **Después de realizar cambios, simplemente ejecute make, esto creará el ejecutable darknet.**
    * ### Ejucion de make(Linux)
        * Solo hazlo en el directorio darknet, antes de hacer, puede configurar tales opciones en el `Makefile`:
            ```PowerShell
                PS Code\>git clone https://github.com/microsoft/vcpkg
                PS Code\>cd vcpkg
                PS Code\vcpkg>$env:VCPKG_ROOT=$PWD
                PS Code\vcpkg>.\bootstrap-vcpkg.bat
                PS Code\vcpkg>.\vcpkg install darknet[full]:x64-windows #remplazar con darknet [opencv-base, cuda, cudnn]: x64-windows para una instalación más rápida de las dependencias
                PS Code\vcpkg>cd ..
                PS Code\>git clone https://github.com/AlexeyAB/darknet
                PS Code\>cd darknet
                PS Code\darknet>.\build.ps1
            ````
    






    
