# Laboratorio \# 21

**Alta disponibilidad con HA**

> Revisión 1.1 2024

## Laboratorio \# 21

**Alta disponibilidad con HA**

Actividades a realizar:

1.  Activación del servicio HA

2.  Configuración del servicio HA

3.  Operación de HA

## Actividad \# 1

**Activación del servicio HA**

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionando el acceso rápido de
**vCenter Server**.

Para activar el servicio distribuido de HA.

Seleccionar en la vista de **Host & Clusters** (1) el cluster
**Production Center** (2), Click en la pestaña Configure (3), Click en
**vSphere Availability** (4)**,** Click en **EDIT** (5).

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Activar el seguro **vSphere HA** (1), habilitar la opción **Enable Host
Monitoring** (2)

<img src="./media/image2.png" style="width:4.39844in;height:3.66175in"
alt="A screenshot of a computer Description automatically generated" />

Se despliega la configuración del servicio

<img src="./media/image3.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Averiguar que elementos están protegidos con el servicio.

Seleccionar el cluster (2), Click en la pestaña **Monitor** (3), en la
sección de **vSphere HA** seleccionar **Summary** (4), notar que el host
primario es el **Host –ESXi_02** (5), y hay dos VMs protegidas.

<img src="./media/image4.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

## Tarea \# 2

**Configuración del servicio HA**

Para esquemas de protección en HA se pueden utilizar los DataStores de
Hearbeat.

Para identificarlos seleccionar el **cluster** (2), Click en la pestaña de
**Monitor** (3), Click en **Hearbeat** (4), tenemos dos datastores de
hearbeat **ICM_Datastore** y **ISCSI_Datastore** (5)

<img src="./media/image5.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En la activación del servicio podemos tener problemas de configuración,
a manera de ejemplo se notan estos dos casos.

Seleccionar el cluster **Production Clusters** (2), Click en **Monitor**
(3), Click en **Configuration Issues** (4)

Observar el mensaje de falta de red de redundancia en ambos hosts

Notar en el inventario que los hosts están alarmados

<img src="./media/image6.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Si seleccionamos en el inventario un **host** (2) y damos click en la
pestaña de **Summary** (3), se muestra el mensaje:

**This host currently has no managment network redundancy** (4)

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Para resolver esta alerta y proporcionar mayor protección a HA

Activar el servicio de administración en una red que tenga ya un puerto
Vmkernel activo, lo haremos con el puerto de vMotion.

Seleccionar el **Host Esxi_01** (1), Click en la pestaña **Configure**
(3), Click en **Virtual Swithes** (4)

Expandir el vSwitch2, Click en los puertos suspensivos del puerto
Vmkernel **vMotion** (5)

Click en **Edit Settings** (6).

<img src="./media/image8.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Habilitar el servicio de **Managment** (1) en el puerto **VMkernel** que
actualmente proporciona el servicio de **vMotion**, OK (2),

1.  <img src="./media/image9.png" style="width:4.61424in;height:2.80642in"
    alt="A screenshot of a computer Description automatically generated" />

Para resolver la alerta tendremos que reconfigurar HA

Esto se logra a nivel del host seleccionar el host **ESXi_01** (2), en
el menú contextual seleccionar **Reconfigure for vSphere HA** (3)

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

La alerta se ha disuelto

<img src="./media/image11.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Realizar la misma operación en el host **Esxi_02**

Seleccionar el host **ESX_02** en el inventario (2), Click en
**Configure** (3), Click en **Virtual switches** (4), Expandir el
**vSwitch2** (5), Click en los puntos suspensivos del puerto Vmkernel de
**vMotion** (6), Click en **EDIT Settings** (7).

<img src="./media/image12.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Activar en servicio de **Managment** (1) en el puerto VMkernel de
**vMotion**

<img src="./media/image13.png" style="width:5.00994in;height:3.06163in"
alt="A screenshot of a computer Description automatically generated" />

Solicitar la reconfiguración

Seleccionar el host **ESXi_02** (2), en el menú contextual seleccionar
la opción **Reconfigure for vSphere HA** (3)

<img src="./media/image14.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Tenemos ya resuelta la alarma en el host **ESXI_02**

<img src="./media/image15.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \#3

**Operación de HA**

Para ver en acción a HA, notemos que máquinas virtuales están en el Host
**ESXi_02**

Seleccionar el Host **ESXI_02** (2), Click en la pestaña de VMs (3),
notar que tenemos dos máquinas virtuales **Linux_04** y **Linux_05** y
una VM de servicios de **clusters vCLS** (4)

<img src="./media/image16.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Para simular una falla, reiniciar el Host. Seleccionar el host **Esxi_02**
(2), en el menú contextual click en **Power** (3), seleccionar **Reboot** (4),
Nota: No usar **Shut Down**

<img src="./media/image17.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En un primer momento se ve que el host se desconecta

<img src="./media/image18.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar el host **ESXI_01**

En unos minutos presenta ya todas más máquinas virtuales que estaban
alojadas en el host **ESXI_02**

<img src="./media/image19.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En el host **ESXi_02** no hay VMs conectadas

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Al restablecerse el estado de energía del host **ESXi_02** se mantiene
sin máquinas virtuales

<img src="./media/image21.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Todas las VMs siguen en el host **ESXI_01**

<img src="./media/image22.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Minutos más tarde DRS detecta que los recursos no están balanceados y
migra las máquinas virtuales

En el host **Esxi_01** permanecen las **Linux_01, Linux_02, Linux_03** y una VM
de servicios

<img src="./media/image23.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En el host **ESXI_02** se muestran activas las máquinas virtuales **Linux_03,
Linux_04** y una VM de servicios, el datacenter efectivamente está
protegido con HA y DRS vigila el rendimiento del cluster

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />
