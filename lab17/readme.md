# Laboratorio \# 17

## Storage vMotion

> Revisión 1.1 2024

### Storage vMotion

Actividades a realizar:

1.  Revisión de condiciones para Storage vMotion

2.  Storage vMotion

3.  Combinar vMotion y Storage vMotion

## Actividad \# 1

**Revisión de condiciones para Storage vMotion**

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionando el acceso rápido de
**vCenter Server**.

Se migrarán los archivos de la VM **Linux_01** mientras opera.

Seleccionar la VM **Linux_01** encenderla desde el menú contextual al
seleccionar **Power On** (5)

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar la VM **Linux_01** en el inventario (2), en el menú
contextual seleccionar **Edit Settings** (4)

<img src="./media/image2.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Observar que los archivos de la VM están en el almacenamiento
**ESXi01**, que es el disco interno del host **ESXi_01**.

<img src="./media/image3.png" style="width:3.46094in;height:3.90862in"
alt="A screenshot of a computer Description automatically generated" />

Las condiciones de almacenamiento de la VM también se pueden observar
cuando está seleccionada la VM y activa la pestaña **Summary**.

<img src="./media/image4.png" style="width:5.88889in;height:3.3125in" />

Seleccionar en el menú contextual de la VM **Linux_01** la opción
**Migrate** (4)

<img src="./media/image5.png" style="width:5.88889in;height:3.3125in" />

Seleccionar **Change storage only** (2), **NEXT** (3)

<img src="./media/image6.png" style="width:4.02865in;height:3.0029in" />

Selecionar la opción de red **Browse** (3)

<img src="./media/image7.png" style="width:3.49219in;height:3.40532in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el port group **dpg-SA-Production** (1), **OK**(2)

<img src="./media/image8.png" style="width:3.26823in;height:3.18693in"
alt="A screenshot of a computer Description automatically generated" />

Asegurarse de que la configuración quede como se ilustra click en **OK** (4)

<img src="./media/image9.png" style="width:2.81788in;height:3.1842in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 2

**Storage vMotion**

Encender la VM y activar la consola para mostrar su operación sin
interrupción mientras se migran sus archivos

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Usar el password `VMware1!`

<img src="./media/image11.png" style="width:5.88889in;height:3.18958in"
alt="A screenshot of a computer Description automatically generated" />

Click en **Apps** (1)

<img src="./media/image12.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Ejecutar la aplicación **Terminal**

<img src="./media/image13.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Emitir el commando Ip route, observar el default Gateway `172.20.10.10`,
ejecutar un **PING** a esa dirección

<img src="./media/image14.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Organizar el escritorio para ver como al hacer la migración de archivos
se mantiene operando sin interrupciones

<img src="./media/image15.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar del menú contextual de la VM Linux_01 (3) la opción **Migrate**
(4)

<img src="./media/image16.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Change storage only** (2), **NEXT** (3)

<img src="./media/image17.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el nuevo datastore, click en **iSCSI-Datastore** (3), Observe
que puede seleccionar el tipo de disco de la VM a obtener (2)

<img src="./media/image18.png"
style="width:5.88889in;height:3.3125in" />

Seleccionar el tipo de disco **Thin provision** (2)

<img src="./media/image19.png"
style="width:5.88889in;height:3.3125in" />

Revisar la configuración final (2), **FINISH** (3)

<img src="./media/image20.png"
style="width:5.88889in;height:3.3125in" />

Observe que la VM sigue operando mientras se da la migración

<img src="./media/image21.png"
style="width:5.88889in;height:3.3125in" />

Se reflejan los cambios de almacenamiento (3)

<img src="./media/image22.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Enseguida se revisa una condición de migración, observar las
especificaciones de almacenamiento de la VM **Linux_03**, está
relacionada con dos discos internos **Storage_ESXI01** y
**Storage_ESXI_02**

<img src="./media/image23.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Para resolver esta condición de asociación a dos Host y que puede
impedir una operación de vMotion

En el menú contextual de la VM seleccionar **Edit Settings** (4)

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Observar que la unidad de CD/DVD está asociada originalmente a una
imagen **ISO** *(Dastastore ISO File)* para la instalación del sistema
operativo, adicionalmente está conectada.

<img src="./media/image25.png" style="width:3.55469in;height:2.86497in"
alt="A screenshot of a computer Description automatically generated" />

Habrá que cambiarla a la opción **Client device** (2)

<img src="./media/image26.png" style="width:3.5026in;height:3.91739in"
alt="A screenshot of a computer Description automatically generated" />

Ahora en la información de resumen de la VM se ve solamente que está
asociada al disco interno del host correspondiente en donde está alojada

## Actividad \#3

### Combinar vMotion y Storage vMotion

<img src="./media/image27.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Con el propósito de hacer una migración combinada de vMotion y Storage
vMotion con la VM **Linux_03**

En el menú contextual de la VM seleccionar **Migrate** (4)

<img src="./media/image28.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar la opción **Change both compute resource and storage** (2),
**NEXT** (3)

<img src="./media/image29.png" style="width:4.27865in;height:3.23661in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el host **ESXi_01** como destino (2), **NEXT** (3)

<img src="./media/image30.png" style="width:4.30469in;height:3.22054in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Thin Provision** (2) y **iSCSI-Datastore** (3) como tipo
de disco y datastore destino. **Next** (4)

<img src="./media/image31.png" style="width:4.42448in;height:3.31017in"
alt="A screenshot of a computer Description automatically generated" />

Determinar como port group **dpg-SA-Production** (2) **Next** (3)

<img src="./media/image32.png" style="width:4.73698in;height:3.56151in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **Schedule vMotion with High Priority** (2), **Next** (3)

<img src="./media/image33.png" style="width:4.73698in;height:3.57905in"
alt="A screenshot of a computer Description automatically generated" />

Revisar la configuración, aceptar **FINISH** (3)

<img src="./media/image34.png" style="width:4.65885in;height:3.47265in"
alt="A screenshot of a computer Description automatically generated" />

Observar los resultados (3)

<img src="./media/image35.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Para asegurar que los servicios de DRS funcionen asegurar que todas las
VMs se pueden mover de un Host a otros, intente que todas las VMs se
pueden mover al host **ESXI_01** y al **host ESXi_02, como se observa en
las siguientes dos imágenes.**

<img src="./media/image36.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image37.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

### 
