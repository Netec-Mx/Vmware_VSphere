# Laboratorio \# 19

**Control de recursos de las máquinas virtuales**

> Revisión 1.1 2024

## Laboratorio \# 19

### Control de recursos de las máquinas virtuales

Actividades a realizar:

1.  Crear condiciones de contención con afinidad de CPU

2.  Revisar estadísticas con condiciones de contención

3.  Uso de Shares para asignar recursos con prioridad

4.  Observar estadísticas con nuevos recursos asignados

5.  Restablecimiento de condiciones operativas normales

## Actividad \# 1

### Crear condiciones de contención con afinidad de CPU

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionando el acceso rápido de
**vCenter Server**.

Para crear condiciones de contención instalaremos y ejecutaremos una
aplicación en las máquinas virtuales **Linux_01** y **Linux_02**

Consideremos el ambiente de laboratorio que se ha venido construyendo

Iniciemos con el lanzamiento de una **VM Linux_01**, en la vista de
**Host & clusters**, seleccionemos la máquina virtual **Linux_01** y
activemos la consola

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Los parámetros que gobiernan los recursos de una máquina virtual están
definidos en la caja de diálogo de especificaciones. Seleccionar en el
menú contextual la opción de **Edit Settings
(4)**

<img src="./media/image2.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Para instalar una aplicación que consuma recursos, montaremos un ISO en
la unidad de CD/DVD. Seleccionar la opción de **Datastore ISO file**

<img src="./media/image3.png" style="width:3.36719in;height:3.45095in"
alt="A screenshot of a computer Description automatically generated" />

Presione el botón **BROWSE (2)** para explorar el disco interno de la
máquina virtual

<img src="./media/image4.png" style="width:3.40365in;height:3.47358in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionemos la unidad interna del host **ESXi_01** llamada
**Storage_ESXI01**

<img src="./media/image5.png" style="width:3.2054in;height:1.51238in"
alt="A screenshot of a computer Description automatically generated" />

En el directorio principal seleccionar el ISO **Classfiles.ISO** (2),
**OK** (3)

<img src="./media/image6.png" style="width:3.26561in;height:3.37934in"
alt="A screenshot of a computer Description automatically generated" />

Aseguremos que la unidad de CD/DVD conectada a la imagen ISO de la VM
esté en estado **Conected (1)**

<img src="./media/image7.png" style="width:3.27344in;height:3.28473in"
alt="A screenshot of a computer Description automatically generated" />

Adicionalmente, en la misma caja de diálogo expanda la sección de CPU y
establezca **Scheduling Affinity (2)** con valor **0**. Esto significa
que todas las operaciones de la máquina virtual se realizarán únicamente
en el **cpu físico 0**. Así entonces se impone una restricción de
recursos. En donde el hipervisor no comparte los recursos de todos los
cpus físicos. **OK** (3)

<img src="./media/image8.png" style="width:3.50781in;height:3.92458in"
alt="A screenshot of a computer Description automatically generated" />

En la consola de la máquina virtual abrir la unidad de DVD que se ha
montado.

<img src="./media/image9.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se muestran al abrir del DVD los archivos relacionados con la aplicación
a utilizar.

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Copiar los archivos al escritorio, para esto sólo basta arrastrarlos con
el mouse.

<img src="./media/image11.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Lanzar la aplicación **Terminal** para emitir comandos en línea

<img src="./media/image12.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Emitir los siguientes comandos:

`ls`

`cd Desktop`

`hmod +x cpubusy.pl`

`perl ./cpubusy.pl`

Se ejecuta una aplicación que realiza “N” operaciones matemáticas por
segundos.

Observar la estadística después de varios minutos al estabilizarse.

<img src="./media/image13.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Realizar los mismos operativos en la máquina **Linux_02**

Montar el ISO en la unidad de CD/DVD, establecer afinidad con el CPU 0

## Actividad \#2

### Revisar estadísticas con condiciones de contención

Se muestran las estadísticas para la **Linux_02**

En este caso cuando ambas máquinas solo usan el **CPU Físico 0**, el
número de operaciones por segundo disminuye y se estabiliza en un valor
menor de operaciones

<img src="./media/image14.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Observar que el número de shares de CPU normal es de 2000 en ambas
máquinas, en la ilustración se muestra la información de la **Linux_01**

<img src="./media/image15.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Con el número de Shares se nota que ambas máquinas realizan en promedio
el mismo número de operaciones matemáticas. Si no tuvieran afinidad
sería mayor el número de operaciones.

<img src="./media/image16.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \#3

### Observar estadísticas con nuevos recursos asignados

Modificar el número de shares en ambas máquinas. Establecer el número de
shares de **Linux_01** en valor de **4000**

<img src="./media/image17.png" style="width:3.72938in;height:4.23849in"
alt="A screenshot of a computer Description automatically generated" />

Establecer el número de shares de **Linux_02** en **500**

<img src="./media/image18.png" style="width:3.29948in;height:3.70986in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image19.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se nota la diferencia de número de operaciones, ahora la VM **Linux_01**
tarda menos tiempo en realizar las operaciones.

Se está asignando el tiempo de operación del CPU 0 de forma diferente
para cada máquina

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

## Tarea \#4

**Restablecimiento de condiciones operativas normales**

Interrumpir la aplicación en ambas máquinas para no afectar el resultado
de laboratorios subsecuentes

<img src="./media/image21.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En ambas máquinas retornar a los valores por default de Shares y
eliminemos la afinidad de CPU.

Si no se elimina la afinidad no se podrá hacer vMotion con la máquina
virtual

<img src="./media/image22.png" style="width:3.3151in;height:3.72743in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image23.png" style="width:3.21573in;height:3.61372in"
alt="A screenshot of a computer Description automatically generated" />