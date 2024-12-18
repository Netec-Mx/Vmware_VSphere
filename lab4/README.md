# Laboratorio \# 4

**Creación de elementos de red con Switches Standard**

> Revisión 1.1 2024

## Laboratorio \# 4

**Creación de elementos de red con Switches Standard**

Actividades a realizar:

1.  Inspeccionar los Switches integrados al Host Esxi-01 y Esxi-02

2.  Agregar un nuevo Switch standard y red en ambos hosts

3.  Migrar las VMs a una nueva red

4.  Realizar prueba de conectividad

5.  Instalar las VMware Tools en la VM_01

## Actividad \# 1

**Inspeccionar los Switches integrados al Host Esxi-01 y Esxi-02**

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: **vclass\Administrator**
>
> Contraseña: **VMware1!**

Abrir una instancia de Firefox, seleccionando el acceso rápido de
vCenter.

Con el propósito de inspeccionar el switch **vSwicht0** integrado al
**host ESXi-01** seleccionar en la vista de Hosts & clusters el **host
Esxi-01** (1), click en pestaña **Configure** (2), click en la sección
de **Networking** (3) en **Virtual Switches** (4).

Observar los elementos de red del **vSwitch0**, a saber, puerto vkernel
de administración con dirección ip del Host (5), **Red VM Network** con
una máquina virtual **VM_01**, Tarjeta de red **vmnic0** (7)

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 2

**Agregar un nuevo Switch standard y red en ambos hosts**

Con el propósito de agregar un switch standard **vSwitch1**, seleccionar
el host **ESX1-01** (1), click en la pestaña de **Configure**, en la
sección de **Networking click** en **virtual switches**. Finalmente,
click en **ADD NETWORKING**

<img src="./media/image2.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En la caja de diálogo, en tipo de conexión, seleccionar **Virtual
Machine Port Group for a Standard Switch** (2), aceptar (3).

<img src="./media/image3.png" style="width:4.26048in;height:3.2224in"
alt="A screenshot of a computer Description automatically generated" />

En el paso **Select a target device** (1) seleccionar: **New Standard
switch** (2) dejando el **MTU** normal de **1500 Bytes** (3), aceptar
(4).

<img src="./media/image4.png" style="width:4.17233in;height:3.15469in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de creación de un Switch standard (1), identificar el botón:
**MOVE DOWN** (1) y seleccionar la tarjeta de red **vmnic2** (2)

<img src="./media/image5.png" style="width:4.31372in;height:3.25115in"
alt="A screenshot of a computer Description automatically generated" />

Presionando en repetidas ocasiones en el botón **MOVE DOWN** (1)
desplazar la tarjeta **vmnic2** a la sección de tarjetas activas (2)

<img src="./media/image6.png" style="width:4.31892in;height:3.27259in"
alt="A screenshot of a computer Description automatically generated" />

En el paso especificaciones de conexión (1) establecer el nombre de la
red **Production** y dejar el **VLAN ID** por default (2), aceptar (3).

<img src="./media/image7.png" style="width:4.33455in;height:3.26685in"
alt="A screenshot of a computer Description automatically generated" />

Revisar la configuración (2) y **Finish** (3)

<img src="./media/image8.png" style="width:4.43725in;height:3.3474in"
alt="A screenshot of a computer Description automatically generated" />

Se actualiza nuestro inventario mostrando el nuevo Switch con sus
componentes, nombre (2), **Red Production** (3), y tarjeta física
asociada (4)

<img src="./media/image9.png" style="width:5.8875in;height:3.31389in" />

Agregar un Switch similar en el host **ESXi-02**

Seleccionar host **ESXi-2** (1), Click en pestaña **Configure**; en la
sección de **Networking** (2) seleccionar: **Virtual Switches** (3),
click en **ADD NETWORKING**

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En la caja de diálogo, en tipo de conexión, seleccionar **Virtual
Machine** **Port Group for a Standard Switch** (2), aceptar (3).

<img src="./media/image3.png" style="width:4.26048in;height:3.2224in"
alt="A screenshot of a computer Description automatically generated" />

En el paso **Select a target device** (1), seleccionar: **New Standard
switch** (2) dejando el **MTU** normal de **1500 Bytes** (3), aceptar
(4).

<img src="./media/image4.png" style="width:4.17233in;height:3.15469in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de creación de un **Switch standard** (1), identificar el
botón **MOVE DOWN** (1) y seleccionar la tarjeta de red **vmnic2** (2)

<img src="./media/image5.png" style="width:4.31372in;height:3.25115in"
alt="A screenshot of a computer Description automatically generated" />

Presionando repetidas ocasiones en el botón **MOVE DOWN** (1) desplazar
la tarjeta **vmnic2** a la sección de tarjetas activas (2)

<img src="./media/image6.png" style="width:4.31892in;height:3.27259in"
alt="A screenshot of a computer Description automatically generated" />

En el paso especificaciones de conexión (1) establecer el nombre de la
red **Production** y dejar el **VLAN ID** por default (2), aceptar (3).

<img src="./media/image7.png" style="width:4.33455in;height:3.26685in"
alt="A screenshot of a computer Description automatically generated" />

Revisar la configuración (2) y aceptar (3)

<img src="./media/image11.png"
style="width:5.8875in;height:3.31389in" />

Se actualiza nuestro inventario mostrando el nuevo Switch con sus
componentes, nombre (2), **Red Production** (3), y tarjeta física
asociada (4)

<img src="./media/image12.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \#3

**Migrar las VMs a una nueva red**

Con el propósito de migrar las conexiones de red del **vSwitch0** al
vSwitch 1 recien creado, seleccionar el **Host ESXi_01** (1),
seleccionar la **VM_01** (2), click en la pestaña **Networks** (3),
click en la red **VM Network** (4), presionar botón derecho y en el menú
contextual seleccionar **Migrate VMS to Another Network** (5)

<img src="./media/image13.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En el paso seleccionar red destino, seleccionar la red de **Production**
(2)

<img src="./media/image14.png" style="width:4.39184in;height:3.32224in"
alt="A screenshot of a computer Description automatically generated" />

En el paso seleccionar máquinas virtuales a migrar (1) click en **SELECT
ALL** (2), aceptar (3)

<img src="./media/image15.png" style="width:4.39184in;height:3.28983in"
alt="A screenshot of a computer Description automatically generated" />

Revisar el resumen del comando, aceptar (3)

<img src="./media/image16.png" style="width:4.5146in;height:3.39948in"
alt="A screenshot of a computer Description automatically generated" />

Revisar que la **VM_01** está ahora conectada a **Production**

<img src="./media/image17.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

De igual forma la **VM_02**

<img src="./media/image18.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 3

**Realizar prueba de conectividad**

Encender ambas máquinas virtuales, seleccionar **VM_01** (1) presionar
botón derecho, click en **Power** (2) y seleccionar **Power On** (3)

<img src="./media/image19.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Realizar algo similar con la **VM_03**, seleccionar **VM_03** (1)
presionar botón derecho, click en **Power** (2) y seleccionar **Power
On** (3)

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Ambas máquinas están encendidas

<img src="./media/image21.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Con el propósito de hacer pruebas observar las especificaciones de la
**VM_01**

Seleccionar **VM_01** (1), botón derecho, seleccionar **Edit Settings**
(2)

<img src="./media/image22.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se muestra la caja de diálogo con las especificaciones de Hardware
virtual de **VM_01**, Verificar tarjeta de red (1), red a la que está
conectada (2) y el status de conexión (3), aceptar (4)

<img src="./media/image23.png" style="width:4.22517in;height:3.4967in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar la **VM_01** (1), click en la pestaña **Summary** (2) y
click en **LAUNCH WEB CONSOLE** para activar una pestaña emergente con
la consola de **VM_01**

<img src="./media/image24.png" style="width:5.88958in;height:3.31319in"
alt="A screenshot of a computer Description automatically generated" />

Si no se muestran al activar el despliegue ventanas emergentes puede
estar bloqueado en el navegador, click en **Options** (1), click en
**allow pop_ups**(2)

<img src="./media/image25.png" style="width:5.88958in;height:3.31319in"
alt="A screenshot of a computer Description automatically generated" />

Aparece la ventana con la consola de la **VM_01**, proporcionar
password: `VMware1!`.

<img src="./media/image26.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Active la aplicación **Terminal**

<img src="./media/image27.png" style="width:4.41667in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Emita el comando (IP a) para averiguar la dirección IP que tiene la
tarjeta de red <u>172.20.10.202/24</u>

<img src="./media/image28.png" style="width:4.42188in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Realice pasos similares para ver la información de la **VM_03**, con
dirección <u>172.20.20.203 /24</u>

<img src="./media/image29.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Pruebe conectividad con la **VM_01** con el comando **Ping**
<u>172.20.10.202</u>

<img src="./media/image30.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

La conexión es exitosa

**Actividad \# 5**

**Instalar las VMware Tools en la VM_01**

Con el fin de instalar las VMware tools en la **VM_01**

En la vista de **Host and clusters** Seleccionar la **VM_01** (1)
presionar el botón derecho, click en **Guest OS** (2), seleccionar
**Install VMware** tools (3).

<img src="./media/image31.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se montará en la unidad de **CD ROM** de la **VM_01** el software de
instalación, se despliega la siguiente notificación

<img src="./media/image32.png" style="width:3.47868in;height:2.27649in"
alt="A screenshot of a computer Description automatically generated" />

También se muestra un mensaje de advertencia que al activarlo se
presenta esta pregunta, seleccionar y aceptar (1)

<img src="./media/image33.png" style="width:4.21115in;height:1.82552in"
alt="A screenshot of a computer Description automatically generated" />

Entrar a la consola de la **VM 01** con el password de `VMware1!`

<img src="./media/image34.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Verificar lo que tenemos en la unidad de **CD ROM**

<img src="./media/image35.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Ejecutar la aplicación **Terminal** y ejecutar los comandos que se
muestran, para tener los archivos de instalación preparados para su
ejecución

<img src="./media/image36.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Ejecutar los comandos indicados para preparar la ejecución del
**script**

<img src="./media/image37.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Ahora se muestra en la **VM_01** las **VMware tools** en ejecución

<img src="./media/image38.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />