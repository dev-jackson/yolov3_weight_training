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
    * ### Ejecucion de make(Linux)
        * Para ejecutar Darknet en Linux, use los ejemplos de este artículo, simplemente use ./darknet en lugar de darknet.exe, es decir, use este comando: `./darknet detector test ./cfg/coco.data ./cfg/yolov4.cfg ./yolov4.weigths` (esto depende de cual sea nuestro entrenamiento)
    * ### Ejecucion en windows(usando CMake)
        * Este es el enfoque recomendado para construir Darknet en Windows.
            1. Instale Visual Studio 2017 o 2019. En caso de que necesite descargarlo
            2. Instale CUDA (al menos v10.0) habilitando la integración VS durante la instalación.
            3. Abra Powershell (Inicio -> Todos los programas -> Windows Powershell) y escriba estos comandos:
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
            ```
        * El uso en windows seria de la siguiente manera: `darknet.exe detector train cfg/coco.data cfg/yolov4.cfg yolov4.conv.137`
    * ## Descargamos pesas(weigths) ya pre-entrenadas
        * Descargue el archivo de peso dentro de la carpeta de `data` usando el comando que se proporciona a continuación
          ```bash
            wget https://pjreddie.com/media/files/darknet53.conv.74
          ```
    * ## Configuracion de dataset personalizado
        * Ya que estas pesas pre-entrendas se na usado para diversas acciones debemos hacer algunos combios para nuestros propositos.
        * Crearemos un achivo yolo-(`el nombre de obejto abreviado o simplemente obj`).cfg y este archivo deve estar en la carpeta `darknet/cfg`.
        * Luego una vez ahi copiamos en contenido del archivo `yolov3.cfg` que esta en la misma carpeta.
        * Una vez echo esto realizaremos cambios dentro de nuestro achivo yolo.
            * ### Clases
                Dentro de nuestro archivo debemos cambiar el numero de clases, buscamos la secciones que tengan `[yolo]` y en las mismas cambiamos el numero de clases en este caso 1 por que solo estoy haciendo esto con una tipo de objeto.
                
            * ### Batch(Lote)
                Este es el número de imágenes elegidas para cada batch(lote). Debe elegir esto de acuerdo con el tamaño de la memoria del sistema (GPU), pero lo ideal es mantenerlo en 64.
                ```bash
                batch=64
                ```
            * ### Subdivisions(Subdivisiones)
                El lote se vuelve a dividir en los bloques de imágenes, consérvelo 16.
                ```bash
                subdivisions=16
                ```
            * ### Alto y ancho(Width and Height)
                Por defecto, ancho = 608 y alto = 608, puede mantenerlo como está, pero si desea cambiarlo, asegúrese de que el número sea un múltiplo de 32(`si no es multiplo obtendra varios errores y lo mas posible el entrenamiento no se pueda concluir`).
            * ### Maximo de lotes(Max batches)
                Este el numero maximo de lotes que desea para el entrenamiento el cual tiene una formula
                Esto no puede ser menos de 4000 incluso si usa 1 clase. Si está usando 2 clases, entonces debería ser 4000 y para 3 clases debería ser 6000. Utilice el resultado de la ecuación en el archivo cfg, que sería número.
                
                La ecuacion o formula seria:
                ```bash
                max_batches = (numero de clases) * 2000
                ```
                Pero como decia anteriormente este numero resultante no debe ser menor a 1 asi usemos una clase en nuestro caso seria:
                ```bash
                max_batches = (1) * 4000
                ```
                **Aviso: lo que se pone es el reultado no la formula, la formula solo es para sacar le valor que deve ir** 
            * ### Pasos(Steps)
                Los seps(pasos) deben ser le `80%` y `90%` del max_batches en nuestro caso seria:
                ```bash
                steps=3200,3600
                ```
            * ### Filtros(Filters)
                Comprobamos si ahi `filters=255` encontrará 3 resultados en la sección `[convolucional]` justo antes de la sección `[yolo]`. Cámbielo con el resultado del siguiente cálculo:
                ```bash
                filters = (clases + 5) x 5
                ``` 
                Como nostros tenesmos solo una clase que es `joystick` el filtro debe ser `filters=18` y si son dos serian `filters=21`

                **Aviso: lo que se pone es el reultado no la formula, la formula solo es para sacar le valor que deve ir**
        * ## Entremamiento de datos personalizado
            Ahora ya tenemos casi todo lo nesesario para hacer el entrenamiento, lo siguiente seria crear archivos para respaldar nuestro entrenamiento
            
            * ### Divicion de test y entreamiento 
                Nesesitamos la lista de direcciones de las imagenes para el entrenamiento.

                Creamos dos archivos dentro de `data`, `train.txt` y `test.txt` dentro de esos archivos deben tener la direccion de las imagenes, es muy importanta que las direcciones sean realtivas a al carpeta `darknet` el ejecutable. Si esto no funciona usar un ruta completa de cada uno de los archivos.

                Esta seria el formato completo en linux:
                ```bash
                /home/user/Documents/yolov3_weight_training/data/images/hqdefault.jpg    
                /home/user/Documents/yolov3_weight_training/data/images/images22.jpg
                /home/user/Documents/yolov3_weight_training/data/images/image20.jpeg
                /home/user/Documents/yolov3_weight_training/data/images/image6.jpeg
                ```
                Forma realiva:
                ```bash
                ../data/images/hqdefault.jpg
                ../data/images/images22.jpg
                ../data/images/image20.jpeg
                ../data/images/image6.jpeg
                ```
                Cualquiera de las dos funcionaria esto podia cambiar dependiendo del sistema que estes realizado este proceso.
                
                Ponga el 80% del total de imágenes en train.txt y el 20% restante en test.txt, pero asegúrese de que no haya ninguna imagen común en estos archivos.

                Si el archivo de imagen dado tiene su archivo de texto de anotación en la carpeta de etiquetas, entonces solo debe estar en train.txt o text.txt, de lo contrario, dará un error durante el entrenamiento.

            * ### Creacion archivo .names
                Necesitamos crear un archivo que tendrá el nombre de todas las clases (como `classes.txt`), así que simplemente cree el archivo `obj.names` dentro de la carpeta de datos. La estructura del archivo debe ser la que se indica a continuación.

                En este caso solo una clase o nombre:
                ```txt
                joystick
                ```
            * ### Creacion archivo .data
                Este archivo contiene las rutas de otros archivos e información sobre el número de clases. Cree obj.data dentro de la carpeta de `data` y guarde el contenido que se indica a continuación.
                ```txt
                classes= 2
                train  = ../data/train.txt
                valid  = ../data/test.txt
                names  = ../data/obj.names
                backup = backup/
                ```
                
                La primera línea es solo el número de clases de objetos.

                La segunda, tercera y cuarta líneas contienen las rutas de los otros archivos, pero nuevamente estas rutas deben ser relativas al ejecutable de darknet.

                La copia de seguridad es la ruta donde se almacenarán los pesos durante el entrenamiento, puede encontrarla dentro del repositorio de darknet. Después de cada 100 iteraciones, se almacenarán los pesos.
            * ### Empecemos el entrenamiento
                Si tienes alguna pc con `GPU` en hora buena sino el servicio de `Google Colap`  para hacer este tipo de actividades.
                Procedemos a ejecutar este comando dentro de la carpeta `darknet`:
                ```bash
                ./darknet detector train ../data/obj.data cfg/yolo-joystick.cfg ../data/darknet53.conv.74
                ```
                El entrenamiento llevará mucho tiempo, así que tómate un trago y descansa.

                Este entrenamiento sigue guardando los pesos después de cada 100 iteraciones en la carpeta de respaldo, por lo que después de cada 100 iteraciones, puede detenerlo y reiniciarlo desde el mismo punto.

                Entonces, suponga que detuvo el entrenamiento después de 500 iteraciones, luego, para reiniciar desde este punto, simplemente ejecute el siguiente comando.
                ```bash
                ./darknet detector train ../data/joystick.data cfg/yolo-joystick.cfg backup/yolo-joystick_500.weights
                ```
            * ### Testing
                

        
    






    
