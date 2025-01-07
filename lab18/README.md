# Práctica 18. Control de cambios con Snapshots

## Objetivos de la práctica:

- Activar una máquina virtual, reconocer su estado actual.
- Crear un Snapshot como 1er punto de retorno.
- Aplicar un primer cambio.
- Crear un Snapshot como 2do punto de retorno.
- Aplicar un segundo cambio.
- Crear un Snapshot como 3er punto de retorno.
- Aplicación del último punto de retorno.
- Uso de la historia de Snapshots.

## Duración aproximada:
- minutos.
<br/>

> Revisión 1.1 2024


## Instrucciones

### Actividad 1. Activar una máquina virtual, reconocer su estado actua

Utilizar en su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionar el acceso rápido de
**vCenter Server**.

Considerar el ambiente de laboratorio que se ha venido construyendo.

Iniciar con el lanzamiento de una **VM Linux_01**.

En la vista de **Host & clusters** (1), seleccionar la máquina virtual
**Linux_01 (3)** y activar la consola.

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Usar en el acceso el password `VMware1!`

<img src="./media/image2.png" style="width:5.88889in;height:3.18958in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se muestra la consola con el estado actual de nuestra máquina
**Linux_01,**. Los cambios se enfocarán en los accesos directos de
aplicaciones en la barra izquierda, con cambios progresivos.

<img src="./media/image3.png" style="width:5.88889in;height:3.18958in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 2 Crear un Snapshot como 1er punto de retorno

En la vista de **Host & Clusters** (1), seleccionr la máquina virtual
**linux_01** (3). Tomar un primer Snapshot del menú contextual **Take
Snapshot** (5).

<img src="./media/image4.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se presenta la ventana de configuración del Snapshot.

Proporcionar nombre: **Linux Desktop default** (1). Incluir en el
Snapshot el registro de memoria de la VM (2), esto asegura en el retorno
a la VM, al usar el Snapshot, tener la VM encendida, si no se activa, al
retornar tendremos la VM apagada. Con las **VM tools** podemos activar
la opción de **Quiesce** para VM intensivas, **CREATE** (3).

<img src="./media/image5.png" style="width:3.79948in;height:2.75037in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 3 Aplicar un primer cambio

A manera de cambio, eliminar del escritorio los accesos directos de los
navegadores.

Se muestra en la imagen el estado a captar en el siguiente Snapshot.

<img src="./media/image6.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 4. Crear un Snapshot como 2do punto de retorno

En la vista de **Host & Clusters** (1), seleccionar la máquina virtual
**Linux_01**(3). Tomar un segundo Snapshot usando el menú contextual
**Take Snapshot** (5).

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se presenta la ventana de configuración del Snapshot.

Proporcionar como nombre: **Desktop without browsers in bar** (1),
incluir en el Snapshot el registro de memoria de la VM (2), **CREATE**
(3).

<img src="./media/image8.png" style="width:3.73177in;height:2.70136in"
alt="A computer screen shot of a message Description automatically generated" />

<br/>

### Actividad 5 Aplicar un segundo cambio

En la máquina virtual aplicamos un segundo cambio. Eliminar los accesos
directos en el desktop de las aplicaciones por default.

<img src="./media/image9.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 6. Crear un Snapshot como 3er punto de retorno

En secuencia, crear un tercer Snapshot. En la vista de **Host & Clusters**
(1), seleccionar la máquina virtual **Linux_01**, tomar un tercer
Snapshot usando el menú contextual **Take Snapshot** (5).

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se presenta la ventana de configuración del Snapshot.

Proporcionar como nombre: **Desktop without apps in bar** (2). Incluir
en el Snapshot el registro de memoria de la VM, **CREATE** (3).

<img src="./media/image11.png" style="width:3.39323in;height:2.44925in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 7. Aplicación del último punto de retorno

Para ilustrar como utilizar la opción de retorno al último Snapshot:

En la VM de la opción **Home**, desplazar el archivo de distribución de
**VM tools** al desktop.

<img src="./media/image12.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Enseguida, si nos interesa revertir los últimos cambios:

En la vista de **Host & Clusters** (1), seleccionar la máquina virtual
**Linux_01**(3). Usar del menú contextual el comando **Revert to
Latest Snapshot** (5).

<img src="./media/image13.png" style="width:5.8875in;height:3.31389in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliegan los términos de advertencia.

Aplicar **REVERT** (1).

<img src="./media/image14.png" style="width:4.40337in;height:2.36599in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Regresar a la consola de la VM **Linux_01** y encontrar que el
archivo de VM tools no se encuentra en el desktop, es decir, se
disolvieron los cambios.

<img src="./media/image15.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 8. Uso de la historia de Snapshots

Tenemos la opción de administrar los Snaphots a través de una consola
especifica.

Seleccionar la máquina virtual **Linux_01** (3), en el menú contextual
seleccionar **Manage Snapshots** (5).

<img src="./media/image16.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Desplegar la historia de Snapshots que se ha integrado con la
aplicación de creación de los mismos en diferentes momentos de los
cambios. Observar el señalamiento (**You are here**), en la historia
puede hacer selección de cualquier punto de retorno.

<img src="./media/image17.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

A manera de ejemplo en la historia de Snapshots podemos ir al primer
punto de retorno.

Esto presenta a la Linux_01 en su estado inicial si aplicamos el comando
**REVERT** (1).

<img src="./media/image18.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Siempre, ante lo que implica llevar una VM a un estado de retorno, se
muestra la correspondiente notificación a manera de advertencia dado que
se perderán los últimos cambios no registrados.

<img src="./media/image19.png" style="width:3.03385in;height:1.55114in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Con la aplicación de REVERT al primer punto de retorno nuestra VM se
presenta en la consola con los elementos de aplicaciones iniciales.

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Retornar a la venta de administración de Snapshots para realizar
acciones varias.

Seleccionar la máquina virtual **Linux_01** (3). En el menú contextual,
seleccionar **Manage Snapshots** (5).

<img src="./media/image21.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En este caso, el indicador (**You are here**) se presenta precisamente
abajo del primer punto de retorno.

<img src="./media/image22.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Retornar a la historia de Snapshots.

Seleccionar el punto de retorno **Desktop without browsers in bar**.

Aplicar el comando **DELETE**.

<img src="./media/image23.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega la advertencia correspondiente.

<img src="./media/image24.png" style="width:3.54427in;height:1.40063in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En nuestra historia de Snapshots se actualizan los puntos de retorno
eliminando uno de ellos de forma específica.

<img src="./media/image25.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

También tenemos a disponibilidad la opción de borrar todos los
Snapshots.

Aplicar el comando de **DELETE All** (1).

<img src="./media/image26.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Es importante considerar que los Snapshots son puntos de retorno de VMs
a los que aplicamos cambios, estos generan en su construcción archivos
adicionales que consumen espacio en disco.

Su uso debe ser breve y al final eliminarse, no se tienen que usar como
elementos de respaldo.

Como es esperado, aparece la advertencia mayor de eliminación de todos
los Snapshots en la historia para esta VM.

<img src="./media/image27.png" style="width:3.50104in;height:1.37448in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Finalmente, se muestra la ventana de administración de Snapshots sin
elementos en su historia.

<img src="./media/image28.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />
