# Laboratorio \# 11

**Instalación de las VMware Tools**

> Revisión 1.1 2024

## Laboratorio \# 11

**Instalación de las VMware Tools**

Actividades a realizar:

1.  Instalación de las VMware Tools

## Actividad \# 1

**Instalación de las VMware Tools**

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionando el acceso rápido de
**vCenter Server**.

Para instalar las VM tools en una máquina Linux de nuestro laboratorio,
click en la VM Linux_01 (1), en el menú contextual seleccionar Guest OS
(2), click en Install VMware Tools (3), esto monta en la unidad de
CD/DVD los archivos de instalación

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega la ventana de información para señalar la operación en la
VM, **MOUNT** (1)

<img src="./media/image2.png" style="width:3.42969in;height:2.22674in"
alt="A screenshot of a computer Description automatically generated" />

En la interfaz cuando está seleccionada la VM en la que se pretender
instalar las **VMware Tools**, con la pestaña Summary activa se muestra un
mensaje de advertencia que se debe atender click **Answer Question**
(2), cuando la VM tiene en el CD/DVD un sistema de archivos montado
previamente

<img src="./media/image3.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se presenta la siguiente pregunta para aceptar cambios en el media de
CD/DVD, seleccionar **Yes** (1), **ANSWER**
(2)<img src="./media/image4.png" style="width:4.23966in;height:1.75434in"
alt="A screenshot of a computer Description automatically generated" />

Se elimina la advertencia, solicitar la consola de la VM, click LAUNCH
THE CONSOLE (4), ingresar con el password `VMware1!`

<img src="./media/image5.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Despliegue el contenido del CD/DVD (1), se mostrarán los files de las VM
tools (2)

<img src="./media/image6.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Activar la aplicación **Terminal**, en la misma emitir los siguientes
comandos, usar el password `VMware1!` cuando se solicite.

`sudo mkdir /mnt/cdrom`

`sudo mount /dev/cdrom /mnt/cdrom`

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

`ls /mnt/cdrom`

`cp /mnt/cdrom/VMwareTools-\*.tar.gz ~/`

`cd ~`

`tar -xzf VMwareTools-\*.tar.gz`

`cd vmware-tools-distrib`

`sudo ./vmware-install.pl`

<img src="./media/image8.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Reiniciar el sistema operativo con el comando sudo reboot

<img src="./media/image9.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Ahora la VM muestra que las VMware tools están en ejecución

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />
