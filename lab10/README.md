# Laboratorio \# 10

**Agregación de recursos en las VMs**

> Revisión 1.1 2024

## Laboratorio \# 10

**Agregación de recursos en las VMs**

Actividades a realizar:

1.  Agregar un disco con formato Thick Provision Eager Zeroed

## Actividad \# 1

**Agregar un disco con formato Thick Provision Eager Zeroed**

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionando el acceso rápido de
**vCenter Server**.

Con el propósito de explorar la agregación de recursos, encender la
**VM_01**, en la vista de **Hosts & Clusters** (1), click en el folder
**Production Servers** (2), seleccionar la VM **VM_01** (3), con el menú
contextual seleccionar **Power** (4) y **Power On** (5)

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En la misma VM seleccionar con el menú contextual la opción **Edit
Settings** (4),

<img src="./media/image2.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

La ventana de especificaciones es el punto central de cambios.

Expandir la opción de **Hard Disk 1** (2) para identificar el tipo de
provisionamiento del disco, **Thin Provision** (3) y el estado de
conexión de la unidad de **CD/DVD**, hacia el ISO de instalación y
conectado (4)

<img src="./media/image3.png" style="width:3.71094in;height:4.17021in"
alt="A screenshot of a computer Description automatically generated" />

Para agregar un disco, click **ADD NEW DEVICE** (1), Click **Hard Disk**
(2)

<img src="./media/image4.png" style="width:3.63802in;height:4.06813in"
alt="A screenshot of a computer Description automatically generated" />

Expandir la sección **New Hard Disk**, determinar un 1 GB de tamaño (1),
establecer provisionamiento **Thick Provision Eager Zeroed** (2)

<img src="./media/image5.png" style="width:2.86719in;height:3.2045in"
alt="A screenshot of a computer Description automatically generated" />

Ahora tenemos dos discos en la VM_01

<img src="./media/image6.png"
style="width:3.49219in;height:3.07727in" />

Para examinar los archivos relacionados con los discos, en la vista de
Almacenamiento (1), click en **Production Datacenter**, click en
**Storage_ESXI01** (3), click en pestaña Files, Click en directorio
**VM_01**, se tienen a la vista los archivos correspondientes **vmdk**
(6)

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />
