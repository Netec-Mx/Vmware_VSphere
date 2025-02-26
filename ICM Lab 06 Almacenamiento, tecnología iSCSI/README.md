# Práctica 6. Almacenamiento, tecnología iSCSI

## Objetivos de la práctica:

- Agregar puerto **VMkernel** para el Storage en Host **ESXI_01**.
- Agregar puerto **VMkernel** para el Storage en Host **ESXI_02**.
- Agregar controladora **iSCSI** basada en software en **Host ESXI_01**.
- Descubrir las **LUNs** desde el **Host ESXI_01**.
- Agregar controladora **iSCSI** basada en software en Host **ESXI_02**.
- Descubrir las **LUNs** desde el **Host ESXI_02**.

## Duración aproximada:
- 20 minutos.


> Revisión 1.1 2024


## Instrucciones

### Actividad 1. Agregar puerto VMkernel para el Storage en Host ESXI_01

Utilizar en su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña:  `VMware1!`

Abrir una instancia de Firefox, seleccionar el acceso rápido de
**vCenter**.

Con el propósito de alcanzar por la red el arreglo de discos en donde
contamos con unidades de almacenamiento **LUNs**, es necesario
establecer una red con un puerto **VMkernel** en cada host para esta
tarea.

Iniciar con el Host **ESXi_01** y realizar una configuración
similar en el Host **ESXI-02**.

Seleccionar el host **ESXi_01** (1). Dar click en pestaña **Configure** (2)
en la sección de **Networking**, click en **Virtual switches** (3).
Expandir el **vSwitch0** (4), click en **ADD NETWORKING** (5).

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Click en **VMkernel** Network Adapter (2), click en **NEXT** (3).

<img src="./media/image2.png" style="width:4.00781in;height:3.01328in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar: **Select an existing standard switch** (2), click en
**vSwitch0** (3), click en **NEXT** (4).

<img src="./media/image3.png" style="width:3.98177in;height:3.00483in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso de propiedades del puerto determinar **IP Storage** como
Nombre de la red (2), click **NEXT** (3).

<img src="./media/image4.png" style="width:4.14844in;height:3.12281in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Establecer la dirección estática (2) con IP **172.20.10.61** y máscara de
red **255.255.255.0**. En la dirección IP del puerto **VMkernel** (3),
click **NEXT** (4).

<img src="./media/image5.png" style="width:4.15365in;height:3.12673in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración del elemento de red click en **FINISH** (1).

<img src="./media/image6.png" style="width:4.3099in;height:3.26025in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Observar la configuración del puerto **VMkernel IP Storage** con la
**vmnic0**.

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 2. Agregar puerto VMkernel para el Storage en Host ESXI_02

Para establecer una configuración similar de red en el Host **ESXi-02**.

Seleccionar el host **ESXi_02** (1). Dar click en pestaña **Configure** (2)
en la sección de **Networking**, click en **Virtual switches** (3).
Expandir el **vSwitch0** (4), click en **ADD NETWORKING** (5).

<img src="./media/image8.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Click en **VMkernel Network Adapter** (2), click en **NEXT** (3).

<img src="./media/image9.png" style="width:4.41927in;height:3.34299in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar: **Select an existing standard switch** (2), click en
**vSwitch0** (3), click en **NEXT** (4).

<img src="./media/image10.png" style="width:4.40885in;height:3.31884in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso de Propiedades del puerto, determinar **IP Storage** como
Nombre de la red (2), click **NEXT** (3).

<img src="./media/image11.png" style="width:4.29948in;height:3.25237in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Establecer la dirección estática (2) con IP **172.20.10.62** y máscara de
red **255.255.255.0** en la dirección IP del puerto **VMkernel** (3),
click **NEXT** (4).

<img src="./media/image12.png" style="width:4.32031in;height:3.25219in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración del elemento de red click en **FINISH** (1).

<img src="./media/image13.png" style="width:4.39368in;height:3.32205in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Observar la configuración del puerto **VMkernel IP Storage** con la
**vmnic0**.

<img src="./media/image14.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 3. Agregar controladora iSCSI basada en software en Host ESXI_01

Configurar una controladora **iSCSI** en el host **ESXi-01**. Dar click en
el **host** (1), click en la pestaña **Configure** (2) en la sección de
**Storage**, click en **Storage Adapters** (3). Dar click en **ADD SOFTWARE
ADAPTER** (4), click en **Add iSCSI Adapter** (5).

<img src="./media/image15.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega el comentario siguiente **OK** (1).

<img src="./media/image16.png" style="width:3.52544in;height:1.52865in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Verificar el status **ENABLE** (5) y el **iSCSI Name** (6), para esto
click en el **host**, click en pestaña **Configure** (2), click en
**Storage adapter**, click en la tarjeta controladora **iSCSI** basada
en Software (4), click en la pestaña **Properties** (5).

<img src="./media/image17.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

## Actividad 4. Descubrir las LUNs desde el Host ESXI_01

Determinar **Dynamic Discovery** (5), click en **ADD** (6).

<img src="./media/image18.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Establecer la dirección IP del Arreglo de disco **172.20.10.15** (1) con
número de puerto **3260** (2), click **OK** (3).

<img src="./media/image19.png" style="width:3.46094in;height:1.99965in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Realizar asociación de puerto de red, click en **Network Port Binding**
(2), click **ADD** (3).

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Click en el puerto **VMkernel IP Storage** (1), **OK** (2).

<img src="./media/image21.png" style="width:3.96671in;height:2.1087in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Es necesario para descubrir las trayectorias, dar click en **RESCAN
ADAPTER** (1).

Revisar las trayectorias de las **LUNS** descubiertas.

<img src="./media/image22.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar las trayectorias de las **LUNS** descubiertas click en
**Devices**.

<img src="./media/image23.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />**  
**

<br/>
<br/>

### Actividad 5. Agregar controladora iSCSI basada en software en Host ESXI_02

Es necesario en el Host **ESXI_02**, repetir las operaciones de adaptador
de Storage para ver también las **LUNs**.

Configuremos una controladora **iSCSI** en el host **ESXi-02**, click en
el **host** (1), click en la pestaña **Configure** (2) en la sección de
**Storage**, click en **Storage Adapters** (3). Click en **ADD SOFTWARE
ADAPTER** (4), click en **Add iSCSI Adapter** (5).

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega el comentario siguiente **OK** (1).

<img src="./media/image25.png" style="width:3.8076in;height:1.66406in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Verificar el status **ENABLE** (5) y el **iSCSI Name** (6), para esto
click en el **host**. Dar click en pestaña **Configure** (2), click en
**Storage adapter**, click en la tarjeta controladora **iSCSI** basada
en Software (4), click en la pestaña **Properties** (5).

<img src="./media/image26.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 6. Descubrir las LUNs desde el Host ESXI_02

**Determinar Dynamic Discovery** (5), click en **ADD** (6).

<img src="./media/image27.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Establecer la dirección IP del Arreglo de disco **172.20.10.15** (1) con
número de puerto **3260** (2), click **OK** (3).

<img src="./media/image28.png" style="width:3.61198in;height:2.08692in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Realizar asociación de puerto de red, click en **Network Port Binding**
(2), click **ADD** (3).

<img src="./media/image29.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Click en el puerto **VMkernel IP Storage** (1), **OK** (2).

<img src="./media/image30.png" style="width:4.54948in;height:2.40065in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image31.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Es necesario para descubrir las trayectorias, dar click en **RESCAN
ADAPTER** (1).

<img src="./media/image32.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar las trayectorias de las **LUNS** descubiertas.

<img src="./media/image33.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Examinar las capacidades de cada **LUN** (3) click en **Devices** (2).

<img src="./media/image34.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />
