# Práctica 16. Migración de VMs entre host ESXi (vMotion)

## Objetivos de la práctica:
 
- Preparación de red para habilitar vMotion.
- Revisión de condiciones para vMotion.
- Migración de VMs entre host ESXi.
  
## Duración aproximada:
- minutos.

<br/>
> Revisión 1.1 2024


## Instrucciones

**Migración de VMs entre host ESXi (vMotion)**

### Actividad 1. Preparación de red para habilitar vMotion

Utilizar en su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionar el acceso rápido de
**vCenter Server**.

Para habilitar vMotion entre los hosts procedemos a crear una red que
tenga habilitado el servicio de vMotion con un puerto Vmkernel.

En la vista de **Host & Clusters** (1), seleccionar el host **ESXI_01**
(2), click en la pestaña **Configure** (3). En la sección de
**Networking**, click en **Virtual switches**, click en **ADD
NETWORKING** (5).

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar **VMKernel Network Adapter** (2), **Next** (3).

<img src="./media/image2.png"
style="width:4.13405in;height:3.09288in" />

<br/>

En el paso **Select target device** (1), click en **New standard
switch** (2), **Next** (3).

<img src="./media/image3.png" style="width:4.10677in;height:3.12605in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En la lista de vmnics, seleccionar la **vmnic1** (2), dar en repetidas
ocasiones el botón **MOVE DOWN** para desplazar la vmnic1 a la sección
de tarjetas activas (**Active adapters**).

<img src="./media/image4.png" style="width:4.33073in;height:3.26817in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Así debería quedar la configuración con **vmnic1** en la sección
**Active adapters** (2), **Next** (3).

<img src="./media/image5.png" style="width:4.28385in;height:3.21289in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Port properties** (1), establecer como nombre del puerto
**vMotion** (2), click en el servicio **vMotion** (3), click **NEXT**
(4).

<img src="./media/image6.png" style="width:4.20052in;height:3.15817in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **IPv4 Settings** (1), dar click en **Use static IPv4 settings**
(2), establecer la dirección ip `172.20.12.51` (3) con máscara de red
`255.255.255.0` (4), **NEXT** (5).

<img src="./media/image7.png" style="width:4.22135in;height:3.1582in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración (2), aceptar **FINISH** (3).

<img src="./media/image8.png" style="width:4.17603in;height:3.13976in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Expandir el **vSwitch2** (1), observar el puerto **VMkernel** (2) con
dirección `172.20.12.51` (3) y **vmnic1** (4).

<img src="./media/image9.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

De forma similar se tiene que configurar el servicio de red con un
puerto VMkernel con vMotion habilitado.

Seleccionar el host **ESXi_02** (2), click en pestaña **Configure** (3)
en la sección de **Networking**, seleccionar **Virtual Switches** (4),
click en **ADD NETWORKING** (5).

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar **VMKernel Network Adapter** (2), **Next** (3).

<img src="./media/image11.png" style="width:4.14323in;height:3.11509in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Select target device** (1), click en **New standard
switch**(2), **Next** (3).

<img src="./media/image12.png" style="width:4.13802in;height:3.13813in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En la lista de vmnics, seleccionar la **vmnic1** (2). Dar en repetidas
ocasiones el botón **MOVE DOWN** (3) para desplazar la **vmnic1** a la
sección de tarjetas activas (**Active adapters**).

<img src="./media/image13.png" style="width:4.1849in;height:3.15812in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Así debería quedar la configuración con **vmnic1** en la sección
**Active adapters** (2), **Next** (3).

<img src="./media/image14.png" style="width:3.8776in;height:2.90102in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Port properties** (1), establecer como nombre del puerto
**vMotion** (2), click en el servicio **vMotion** (3), click **NEXT**
(4).

<img src="./media/image15.png"
style="width:3.8724in;height:2.91147in" />

<br/>

En el paso **IPv4 Settings** (1), hacer click en **Use static IPv4 settings**
(2), establecer la dirección ip `172.20.12.52` (3) con máscara de red
`255.255.255.0` (4), **NEXT** (5).

<img src="./media/image16.png" style="width:3.9052in;height:2.94705in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración (2), aceptar **FINISH** (3).

<img src="./media/image17.png"
style="width:3.87438in;height:2.92379in" />

<br/>

Expandir el **vSwitch2** (1), observar el puerto **VMkernel** (2) con
dirección `172.20.12.52` (3) y **vmnic1** (4).

<img src="./media/image18.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 2. Revisión de condiciones para vMotion

En la vista de **Hosts & Clusters** (1), seleccionar el host **ESXi_01**
(2), click en la **VM Linux_02** en el menú contextual encender la VM
con **Power ON** (5).

<img src="./media/image19.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el menú contextual de la VM, seleccionar **Edit Settings** (4).

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la red. Abrir el menú de redes (2), click en **Browse** (3).

<img src="./media/image21.png" style="width:3.85677in;height:3.76131in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar el port group **dpg-SA-Production** (1), **OK** (2).

<img src="./media/image22.png" style="width:3.23694in;height:3.11892in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar que la configuración quede tal como se ilustra, port group
**dpg-Production**, **Connected** (2), **Connect at power On** (3),
**OK** (4).

<img src="./media/image23.png" style="width:3.24392in;height:3.62934in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 3. Migración de VMs entre host ESXi

Para aplicar la migración de la VM encendida y demostrar que en la
migración la VM opera sin interrumpir su servicio. Activar la consola de
la VM **Linux_02** (1).

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Usar el password `VMware1!`.

<img src="./media/image25.png" style="width:5.88889in;height:3.18958in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el desktop click en **APs** (1).

<img src="./media/image26.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ejecutar la aplicación **Terminal** (1).

<img src="./media/image27.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Emitir el comando **ip route** (1). Identificar la dirección del default
Gateway `172.20.10.10` (2), dar **ping** extendido a esa dirección (3).

<img src="./media/image28.png"
style="width:5.88889in;height:3.3125in" />

<br/>

Se mantiene con respuesta de la dirección referida.

<img src="./media/image29.png"
style="width:5.88889in;height:3.3125in" />

<br/>

Organizar su desktop principal para observar la VM operando sin
interrupción mientras se migra la VM.

Seleccionar la VM **Linux_02** (3), en el menú contextual seleccionar
**Migrate** (4)

<img src="./media/image30.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar **Change compute resource only** (2), **NEXT** (3).

<img src="./media/image31.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Establecer como host destino **ESXi_02** (2), **NEXT** (3).

<img src="./media/image32.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar como red destino la **dpg-SA-Production** (2), **Next** (3).

<img src="./media/image33.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar **Schedule vMotion with high Priority** (2), **NEXT** (3).

<img src="./media/image34.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración de migración (2), aceptar **FINISH** (3).

Observar que mientras se migra la VM, el servicio sigue funcionando sin
interrupción.

<img src="./media/image35.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ahora se observa operando la VM en el host **ESXi_02**.

<img src="./media/image36.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Interrumpir la aplicación PING en la VM.

<img src="./media/image37.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

La operación de vMotion será totalmente necesaria para otros servicios
como **DRS** y **Fault tolerance**.
