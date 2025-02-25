# Práctica 13. Administración de plantillas y clones

## Objetivos de la práctica:

- Crear una plantilla.
- Crear un archivo de especificaciones.
- Crear una VM a partir de una platilla.
- Clonar una VM operacional.

## Duración aproximada:
- 30 minutos.
<br/>

> Revisión 1.1 2024

## Instrucciones

### Actividad 1. Crear una plantilla

Utilizar en su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionar el acceso rápido de
**vCenter Server**.

Para convertir una máquina virtual a una plantilla es necesario apagarla.

En la vista de **Hosts & Clusters** (1), seleccionar el folder de
servidores **Production Servers** (2). Dar click en la máquina **virtual
Linux_01** (3), con el menú contextual, seleccionar **Power** (4) y dar
click en **Shut Down Guest OS** (5). Dado que ya tenemos instaladas las
VM Tools es posible apagar de forma ordenada la VM.

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega la advertencia de la operación, confirmar **Yes** (1).

<img src="./media/image2.png" style="width:4.18722in;height:1.62489in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar la VM **Linux_01** (3). En el menú contextual
seleccionar **Convert to Template** (4).

<img src="./media/image3.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

La advertencia en este caso se despliega dado que desaparecerá del
inventario la VM y tendremos una plantilla en su lugar. Aceptar **Yes**
(1).

<img src="./media/image4.png" style="width:4.04452in;height:1.44878in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ahora, tendremos el inventario en la vista de **VMs & Templates** (1),
dentro del folder de VMs llamado **Production VMS & Templates** (2) la
plantilla **Linux_01** (3). Verificar en la parte central con la pestaña
de **Summary** los detalles de la nueva plantilla.

<img src="./media/image5.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 2. Crear un archivo de especificaciones

Para crear máquinas virtuales que sean similares con detalles
específicos para cada una, generar un archivo de especificaciones.

Dar click en el menú principal (1) y seleccionar **Policies and Profiles**
(2). 

<img src="./media/image6.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar **VM customization Specifications** (1), dar click en **New**
(2).

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el campo de **Name** establecer **Linux-spec** (2). Instaurar que es
una VM con **SO Linux** (3). Next (4).

<img src="./media/image8.png" style="width:4.23872in;height:2.76302in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Computer name** (1), fijar **Use the virtual machine
name** (2). Establecer un dominio inicial de **vclass.local** (3).
Next (4).

<img src="./media/image9.png" style="width:4.25781in;height:2.78578in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Time Zone** (1), establecer **Area US** (2). Seleccionar de
la lista desplegable **Pacific** (3). Next (4).

<img src="./media/image10.png" style="width:4.01615in;height:2.63281in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Customization Script**, dar click en **Next** (1).

<img src="./media/image11.png" style="width:4.06264in;height:2.68316in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Network**, establecer **Manually select customs settings**
(2), **NIC1** (3). Next (4).

<img src="./media/image12.png" style="width:4.0651in;height:2.67481in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **DNS settings** (1), establecer como **Primary DNS server
172.20.10.10** (2). En **DNS Search path**s **vclass.local** (3).
Next (4).

<img src="./media/image13.png" style="width:4.10677in;height:2.67701in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración final. Finish (3).

<img src="./media/image14.png" style="width:4.41406in;height:2.88232in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega un nuevo archivo de especificaciones en el inventario.

<img src="./media/image15.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

### Actividad 3. Crear una VM a partir de una plantilla

Proceder a crear una máquina virtual a partir de la plantilla
**Linux_01**, con las especificaciones recién creadas.

En la vista de **VMs & Templates** (1), seleccionar el folder
**Production VMs & Templates** (2). Seleccionar la plantilla
**Linux_01** (3), en el menú contextual, dar click en **New VM from this
template** (4).

<img src="./media/image16.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Establecer como nombre **Linux_02** y definir su ubicación en el folder
**Production VMs & Templates** (3). Next (4).
<img src="./media/image17.png" style="width:4.26823in;height:3.22101in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Select a compute resource**, desplegar la lista de Hosts
(2) y seleccionar el Host **ESXi_01** (3). Next (4).

<img src="./media/image18.png" style="width:4.22135in;height:3.17383in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar el DataStore en el que se grabarán los archivos de la VM
**iSCSI-Datastore** (2). Next (3).

<img src="./media/image19.png" style="width:4.24219in;height:3.1895in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Select clone Options**, activar las opciones **Customize
the operating system** (2) y **Power on virtual machine after creation**
(3). Next (4).

<img src="./media/image20.png" style="width:4.1849in;height:3.14642in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Customize Guest OS** (1), dar click en **Linux-spec** (2).
Next (3).

<img src="./media/image21.png" style="width:4.1849in;height:3.13092in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar opciones (2). Finish (3).

<img src="./media/image22.png" style="width:4.1849in;height:3.15812in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En la vista de **Hosts & Clusters** (1), dar click en la carpeta
**Production Servers** (2), se puede observar en el host ESXi_01 la
existencia de la VM **Linux_02** (3) que se ha encendido (4) y que tiene
las VMware tools “On running”, lo que significa que se a terminado el
proceso de creación de la VM.

<img src="./media/image23.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

### Actividad 4. Clonar una VM operacional

Alternativamente, se pueden crear VMs con la opción de clonación en la
que es irrelevante el estado de la VM original.

Crear la VM **Linux_01** a partir de la nueva **VM Linux_02**.

Seleccionar en el inventario la nueva **VM Linux_02** (1), en el menú
contextual dar click en **Clone** y seleccionar **Clone to virtual Machine** (3).

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Establecer como nombre **Linux_01** (2). Definir el folder **Production
VMs & Templates** como punto para su almacenamiento en el inventario
(3). Next (4).

<img src="./media/image25.png" style="width:4.74219in;height:3.57765in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar el host **ESXi_01** (2) para su registro. Next (3).

<img src="./media/image26.png" style="width:3.73681in;height:2.83056in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

El datastore en donde se almacenarán sus archivos será
**iSCSi-Datastore** (2). Next (3).

<img src="./media/image27.png" style="width:3.78385in;height:2.84836in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Activar ambas opciones para la customización **Customize the operating
system** (2) y **Power on virtual machine after creation** (3). Next
(4).

<img src="./media/image28.png" style="width:3.78906in;height:2.81034in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Determinar el archivo de especificaciones **Linux-spec**. Next (3).

<img src="./media/image29.png" style="width:4.24219in;height:3.17773in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar el resumen de las especificaciones (2). Finish (3).

<img src="./media/image30.png" style="width:4.20052in;height:3.16991in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ahora tenemos una nueva máquina en el inventario **Linux_01** con las
VMware tools funcionando.

<img src="./media/image31.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />


