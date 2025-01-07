# Práctica 1. Acceso al escritorio remoto, exploración y configuración incial en el host ESXi y VCenter Server

## Objetivos de la práctica:
- Acceder al escritorio remoto (espacio de trabajo continuo).
- Conectar, explorar y configurar el host ESXi.
- Conectar, explorar y configurar el vCenter Server.

## Duración aproximada:
- minutos.

> Revisión 1.1 2024

## Instrucciones

## Actividad \# 1

### Acceso al escritorio remoto (espacio de trabajo continuo)

En cada uno de los laboratorios, se sugiere el acceso al escritorio
remoto, para esto, si no lo tiene activo en el momento, utilizar de su
sistema la herramienta de “Conexión a escritorio remoto” con la
dirección y puerto que le proporcionará su instructor; utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1` 

a manera de ejemplo:

<img src="./media/image1.png" style="width:1.82478in;height:2.21484in"
alt="A screenshot of a computer Description automatically generated" />
<img src="./media/image2.png" style="width:1.81546in;height:2.22951in"
alt="A screenshot of a computer screen Description automatically generated" />

Se recomienda guardar su identidad y credenciales para futuros accesos.

Se presentará el escritorio remoto con el browser de Firefox.

<img src="./media/image3.png" style="width:3.16969in;height:1.8062in"
alt="A blue screen with a square window Description automatically generated with medium confidence" />

Abrir una instancia del browser Firefox, en la interfaz encontrará 3
accesos cortos en la barra de herramientas, a saber, **vCenter**, **Esxi-01**,
**Esxi-02**, utilizarlos según se requiera o indique.

<img src="./media/image4.png" style="width:5.88976in;height:3.31102in"
alt="A screenshot of a computer Description automatically generated" />

## Actividad \# 2

**Conexión, exploración y configuración del host ESXi**

Dar click en el acceso corto del host **ESXi-01**

Proporcionar como:

User: `root`

Password: `VMware1!`

Click en botón **LOGIN**

<img src="./media/image5.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se presentará la interfaz del **host client**, en la misma de pueden
distinguir el inventario por la izquierda (1), la información de versión
por el centro (2) y las estadísticas de recursos por la derecha (3).

<img src="./media/image6.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Dar click en **Virtual Machines** (1), y observar que tenemos en el inventario
una máquina virtual (2) que se llama **VM_01**.

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Dar click en **Storage** (1), observar que tenemos un datastore local (2) que se
llama **Storage_ESXi01**. este es un disco virtual **VMFS** interno del
servidor.

<img src="./media/image8.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Hacer click en **vSwitch** (1), observar del lado derecho los elementos del
**vSwitch0**. Switch interno del **host ESXi**, con sus elementos a saber: red
**VM Network** (2), con una máquina virtual asociada **VM_01*, (3) un puerto
**VMkernel** con dirección 172.20.10.51, que se utiliza para administrar el
Host **ESXi**, y una tarjeta de red llamada **vmnic 0** (4).

<img src="./media/image9.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

**Asociación del host ESXi a un dominio:**

Dar Click en **Manage** (1), click en Security & Users (2), click en **Join
domain** (3)

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En la ventana emergente proporcionar la información de dominio, **Username**
y **password**: `VMware1!`, click en **Join Domain**, el host se asocia al dominio
**vclass.local**

<img src="./media/image11.png" style="width:3.79427in;height:2.39389in"
alt="A screenshot of a computer Description automatically generated" />

**Activar el servicio de SSH**

Dar Click en **Manage** (1), Click en **Services** (2), Click en **TSM-SSH** (3),
Observar que el servicio está detenido (4), Click en **Start** (5).
Observar que el servicio está detenido (4), Click en **Start** (5).

<img src="./media/image12.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Observe que se ha iniciado el servicio (1) y (2).

<img src="./media/image13.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />**  
**

**Activar el servicio de NTP**

Dar click en **Manage** (1), **System** (2), **Time & date** (3), observe que el
servicio no está activo (4), Click en **Edit NTP Settings** (5).

<img src="./media/image14.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Configurar en la ventana emergente, Click en **Use Network Time Protocol**
(enable NTP Client) (1), seleccione: **Start and stop with host** (2),
proporcione la dirección Ip del **NTP server**, <u>172.20.10.2</u> (3)

<img src="./media/image15.png" style="width:4.03226in;height:1.87152in"
alt="A screenshot of a computer Description automatically generated" />

Como resultado estará el servicio configurado, pero detenido.

<img src="./media/image16.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Para activarlo, dar click **Manage** (1), **click Services** (2), click **ntpd** (3),
observe que está detenido (4), click **Start** (5).

<img src="./media/image17.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

**  
**

El servicio ya está activo

<img src="./media/image18.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Enseguida, hacer click en **Manage** (1), **click System** (2), **Click Time & date** (3),
observe que requiere actualización la interfaz, Click **Refresh** (5).

<img src="./media/image19.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

**  
**

Finalmente, se presenta ya activo NTP en la interfaz.

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

**Asignación de Licencia al Host Esxi**

Dar click en **Manage**(1), click **Licensing** (2), **Assign Licence** (3).

<img src="./media/image21.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />**  
**

En la ventana emergente proporcionar la licencia que le otorgue el
instructor y de click en **Check License**.

<img src="./media/image22.png" style="width:4.60677in;height:2.30339in"
alt="A screenshot of a computer Description automatically generated" />

Click en **Assign Licence**.

<img src="./media/image23.png" style="width:4.69507in;height:2.33073in"
alt="A screenshot of a computer Description automatically generated" />

Aparece la interfaz con la licencia activa.

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />



## Actividad \# 3

Conexión, exploración y configuración del vCenter Server.

En la interfaz del browser Firefox click en el acceso directo del
**vCenter** (1), proporcionar como user: <administrator@vsphere.local> y
Password: **VMware1!** (2), Click en **LOGIN** (3).

<img src="./media/image25.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Verificar que no tiene licencia asignada el **vCenter Server** (1).

<img src="./media/image26.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Asignar licencia al Click en el **vCenter Server** sa-vcsa-01.vclass.local
(1), click en **Configure** (2), **Licensing** (3), **Assign Licence** (4).

<img src="./media/image27.png"
style="width:5.8875in;height:3.31389in" />

Proporcionar la licencia que le otorgue el instructor en la ventana
emergente.

<img src="./media/image28.png" style="width:4.67407in;height:2.61198in"
alt="A screenshot of a computer Description automatically generated" />

Observar que se lista la licencia en la interfaz.

<img src="./media/image29.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
