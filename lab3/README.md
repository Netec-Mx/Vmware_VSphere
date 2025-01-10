# Práctica 3. Integración de hosts al inventario y configuración del protocolo NTP en un host con vCenter Server

## Objetivos de la práctica:

- Incluir en el inventario al **host ESXi-01**.
- Incluir en el inventario al **host ESXi-02**.
- Configurar NTP en el host **ESXI-02**.

## Duración aproximada:
- 30 inutos.


> Revisión 1.1 2024


## Instrucciones

### Actividad 1. Incluir en el inventario al host ESXi-01

Utilizar en su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionar el acceso rápido de
**vCenter**.

En vista de **Host & Clusters** seleccionar el folder para alojar a los
servidores **Production servers** (1), presionar botón derecho, en el
menú contextual seleccionar: **Add Host** (2).

<img src="./media/image1.png" style="width:5.8875in;height:3.31389in" />

<br/>

En el paso Nombre y ubicación, proporcionar el nombre completo de
dominio **sa-esxi-01.vclass.local** (1).

<img src="./media/image2.png" style="width:4.48698in;height:3.39823in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En especificaciones de conexión, proporcionar User name: **root** y
Password: **VMware1!** (1), aceptar (2).

<img src="./media/image3.png" style="width:4.48177in;height:3.39428in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega una ventana de advertencia de seguridad, aceptar (1).

<img src="./media/image4.png" style="width:3.84635in;height:2.71507in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso de Resumen, revisar configuración, aceptar (1).

<img src="./media/image5.png" style="width:4.53906in;height:3.42098in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Proporcionar la licencia que le otorgó su instructor **license 1** (2),
aceptar (3).

<img src="./media/image6.png" style="width:4.27419in;height:3.22135in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Activar el modo **lockdown mode** para proteger el acceso al **host**
sólo desde la consola local y **vCenter Server** (2), aceptar (3).

<img src="./media/image7.png" style="width:4.28385in;height:3.24439in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Definir la ubicación de las máquinas virtuales en el folder **Production
VMs & Templates** (3), aceptar (4).

<img src="./media/image8.png" style="width:4.14726in;height:3.15365in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar el resumen de la configuración, aceptar (2).

<img src="./media/image9.png" style="width:4.15365in;height:3.14206in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se presenta nuestro servidor **Esxi_01** con su **VM_01**.

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 2. Incluir en el inventario al host ESXi-02

En vista de **Host & Clusters**, seleccionar el folder para alojar a los
servidores **Production Servers** (1), presionar botón derecho en el
menú contextual y seleccionar: **Add Host** (2).

<img src="./media/image11.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso Nombre y ubicación, proporcionar el nombre completo de dominio
**sa-esxi-02.vclass.local** (1).

<img src="./media/image12.png" style="width:4.1849in;height:3.16192in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En especificaciones de conexión, proporcionar User name: **root** y
Password: **VMware1!** (1), aceptar (2).

<img src="./media/image13.png" style="width:4.19531in;height:3.14648in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega una ventana de advertencia de seguridad, aceptar (1).

<img src="./media/image14.png" style="width:3.6865in;height:2.57031in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso de Resumen, revisar configuración, aceptar (1).

<img src="./media/image15.png" style="width:3.72135in;height:2.81505in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Proporcionar la licencia que le otorgó su instructor **license 1** (2),
aceptar (3).

<img src="./media/image16.png" style="width:3.85992in;height:2.91927in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Activar el modo **lockdown mode** para proteger el acceso al host solo
de la consola local y **vCenter Server** (2), avanzar (3).

<img src="./media/image17.png" style="width:3.86719in;height:2.92883in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Definir la ubicación de las máquinas virtuales en el folder **Production
VMs & Templates** (3), aceptar (4).

<img src="./media/image18.png" style="width:4.17969in;height:3.13732in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar el resumen de la configuración, aceptar (2).

<img src="./media/image19.png" style="width:4.19531in;height:3.15809in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se presenta nuestro servidor **ESXi**.

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Si expandimos los servidores podremos apreciar sus **VMs** integradas
**VM_01 y VM_03**.

<img src="./media/image21.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Al cambiar a la vista de **VMs &Templates** (1), se nota el folder
**Production VMs & Templates** (2) con las **VMs** (3).

<img src="./media/image22.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 3. Configurar NTP en el host ESXI-02

En la vista de **Host& Clusters** se nota el host **ESXi_01** (2) con
unas alertas de seguridad (3) especificando que se tiene **ESXi Shell**
y **SSH** activos, en las mismas se ven las ligas de **Actions** (4).

<img src="./media/image23.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Para eliminarlas, dar click en las ligas de **Actions** y click sobre:
**Suppress Warning**.

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega la advertencia correspondiente, es un tema de seguridad del
que uno tiene que estar consciente, aceptar (1).

<img src="./media/image25.png" style="width:3.82552in;height:1.98286in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se disuelven dichas alertas.

<img src="./media/image26.png"
style="width:5.8875in;height:3.18681in" />

<br/>

Para configurar NTP en el **host ESXi-02**, seleccionarlo (1). Hacer click en
la pestaña **Configure** (2), en la sección de **System** (4), click en
**Time Configuration** (5), click en **ADD SERVICE** (6) y seleccionar
**Network Time Protocol** (7).

<img src="./media/image27.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Aparece el servicio en ejecución (**Running**).

<img src="./media/image28.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Para cambiar la política de inicio de funcionamiento del protocolo,
Click en: **Host ESXi_02** (1). Hacer click en pestaña **Configure** (2), en
la sección de **System** (3). Click en: **NTP Daemon**(4), notar que la
política actual es iniciar en modo manual (5), click en: **EDIT STARTUP
POLICY** (6).

<img src="./media/image29.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar **Start and Stop with Host** (1), aceptar (2).

<img src="./media/image30.png" style="width:3.70052in;height:2.05474in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Observar que ahora ha cambiado la política para iniciar al protocolo
cuando el host arranque (3).

<img src="./media/image31.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />
