# Práctica 9. Administración de máquinas virtuales en el inventario del vCenter Server

## Objetivos de la práctica:

- Crear una máquina virtual desde el vCenter Server.
- Eliminar una máquina virtual del inventario.
- Registrar una máquina virtual en un host.
- Eliminar el disco de una máquina virtual.

## Duración aproximada:
- 10 minutos.
<br/>

> Revisión 1.1 2024

## Instrucciones

### Actividad 1. Creación de una máquina virtual desde el vCenter Server

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionar el acceso rápido de
**vCenter Server**.

El proceso de incluir máquinas virtuales se puede realizar a partir de
diferentes opciones, utilizar el vCenter Server para hacerlo.

En la vista de máquinas virtuales (1), dar click en el folder de
**Production VMs & Templates** (2). En el menú contextual seleccionar
**New Virtual Machines** (3).

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el primer paso del proceso, seleccionar el tipo de creación a
utilizar, dar click en **Create a new virtual machine** (2) Next (3).

<img src="./media/image2.png" style="width:4.30469in;height:3.26452in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En selección de ***Nombre y folder***, establecer el nombre **Linux-Empty**
(2), esta será una VM que agregaremos al inventario estableciendo su
arquitectura, pero sin recorrer todos pasos del sistema operativo guest
para su  instalación final, será una VM de Linux.

Click en folder **Production VMs & Templates (3).** Next (4).

<img src="./media/image3.png" style="width:4.55469in;height:3.43718in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Para su funcionamiento la alojaremos en el **host ESXi_01** (3). Next
(4).

<img src="./media/image4.png" style="width:4.48177in;height:3.36549in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Importante, seleccionar el DataStore en el que quedarán sus archivos,
en este caso se usará ya un datastore compartido que permitirá,
posteriormente hacer vMotion con esta VM. Dar click en **iSCSI-Datastore** (2).
Next (3).

<img src="./media/image5.png" style="width:4.3724in;height:3.29962in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

La compatibilidad la dejaremos en su valor por default, versión 8 (2).
Next (3).

<img src="./media/image6.png" style="width:4.33594in;height:3.28822in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En la selección del sistema operativo **guest**, seleccionar **Linux** (2) con
distribución **Ubuntu** (3). Next (4).

<img src="./media/image7.png" style="width:4.36719in;height:3.27806in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

El paso de customización del hardware tiene varios detalles a
determinar con cuidado.

Dejar los valores por default de requerimientos de una distribución
Linux de Ubuntu a 64 bits.

Expandir la opción de **New Disk** (3), seleccionar el provisionamiento
**Thin Provision** (4) para que se refleje en disco solo el espacio
realmente ocupado.

**Seleccionar la red Production (5)**.

En la lista de opciones de CD/CVD, seleccionar DataStore **ISO File** (6).

<img src="./media/image8.png" style="width:4.33073in;height:3.24003in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar el DataStore **local Storage_ESXi01** (1). OK (2).

<img src="./media/image9.png" style="width:4.23545in;height:2.03385in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En la estructura de disco local, seleccionar el ISO de **Ubuntu** (2).

<img src="./media/image10.png" style="width:3.1in;height:3.19375in" />

<br/>

Asegurarse que la unidad de CD/DVD esté conectada al arrancar la
máquina virtual (3). Next (5).

<img src="./media/image11.png" style="width:4.22135in;height:3.18563in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración final. Finish (3).

<img src="./media/image12.png" style="width:4.3202in;height:3.21615in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Observar la configuración de la VM que se ha creado, dar click en
**Linux-Empty** (2) y en la pestaña **Summary** (2). Revisar los objetos
relacionados **host** (3), **Red** (4) y **Storage** (5).

<br/>

<img src="./media/image13.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 2. Eliminación de una máquina virtual del inventario

Proceder a eliminar la VM del inventario, esta operación no afecta sus
archivos.

En la vista de VMs & Plantillas, dar click en **Linux-Empty**, en el menú
contextual seleccionar Remove from **Inventory** (3).

<img src="./media/image14.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se presenta la advertencia en espera de confirmación, dar click en Yes
(1).

<img src="./media/image15.png" style="width:4.45552in;height:1.61719in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

La máquina desaparece del inventario de vCenter Server.

Revisar el datastore en donde se encuentran los archivos de la VM para
registrarla en otro **host ESXI**.

En la vista de almacenamiento (1), dar click en **iSCI-Datastore** (2). Dar click en la pestaña **Files** (3), seleccionar el directorio **Linux-Empty**, se listan los archivos intactos de la **VM** (5).

<img src="./media/image16.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 3. Registro de una máquina virtual en un host

Para registrarla en un host diferente, dar click en el archivo **vmx** (5) y
presionar el botón **REGISTER VM**.

<img src="./media/image17.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Determinar si se modifica el nombre (2), seleccionar **folder** (3).
Next (4).

<img src="./media/image18.png" style="width:4.21615in;height:3.17378in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Momento de seleccionar el host al cual se asocia, dar click en ESXI_02.
Next (4).

<img src="./media/image19.png" style="width:4.34635in;height:3.28783in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración final. Finish (2).

<img src="./media/image20.png" style="width:4.35156in;height:3.28785in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ahora, se despliega la VM en la estructura del **host ESXI_02** (4).

<img src="./media/image21.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Tarea 4. Eliminación del disco de una máquina virtual

Cuando se requiere borrar permanentemente una VM del inventario y
disco.

Seleccionar **Linux-Empty** (4) del menú contextual, dar click en **Delete
from disk** (5).

<img src="./media/image22.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se muestra la advertencia correspondiente en espera de confirmación,
dar click en Yes (1).

<img src="./media/image23.png" style="width:3.39258in;height:1.50781in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ahora, en el datastore ya no aparecen los archivos de la **VM** (5), este
es un proceso no reversible.

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />
