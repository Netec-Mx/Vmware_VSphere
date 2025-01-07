# Práctica 20. Balanceo de carga en el cluster con DRS

## Objetivos de la práctica:

- Crear un cluster.
- Establecer condiciones funcionales con DRS.
- Integrar Hosts al cluster.
- Activar el DRS en el cluster, Operación manual de DRS.
- Operación automática de DRS.

## Duración aproximada:
- minutos.
<br/>

> Revisión 1.1 2024

## Instrucciones

### Actividad 1. Creación de un Cluster

Utilizar en su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionar el acceso rápido de
**vCenter Server**.

Para configurar y aprovechar los servicios distribuidos, habrá que crear
un cluster.

Seleccionar el datacenter **Production Datacenter** (2).En el menú
contextual, seleccionar la opción **New Cluster** (3).

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Proporcionar el nombre al cluster como **Production Cluster** (2). No
activar ningún servicio.

Desactivar la opción **Manage all host in the cluster with a single
image** (4), **Next** (5).

En este recuadro se pueden activar todos los servicios de inicio.

<img src="./media/image2.png" style="width:4.79948in;height:3.59072in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración del cluster, **Finish** (3).

<img src="./media/image3.png" style="width:4.3099in;height:3.22058in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 2. Establecer condiciones funcionales para DRS

DRS depende para su operación del servicio de classic vMotion.

Revisar en cada host que tengamos el puerto VMkernel con el servicio
vMotion activo.

Verificar en el host **ESXi_01**, en la opción de **Vmkernel adapters**
(5), puerto **vmk2** (6).

<img src="./media/image4.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Verificar configuración similar en el host **ESXi_02**.

<img src="./media/image5.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 3. Integración de Hosts al cluster

Integrar los servidores al cluster.

Arrastrar con el mouse el Host **Esxi_01** sobre el cluster **Production
Cluster**.

Arrastar con el mouse el Host **ESXi_02** sobre el cluster **Production
Cluster**.

<img src="./media/image6.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Observar que el cluster despliega los host y máquinas virtuales a la
misma altura sin mostrar jerarquía entre ellos.

Para ver que VMs están en cada Host, seleccionar un host y la pestaña de
**VMs**.

<br/>
<br/>

### Tarea 4. Activación de DRS en el cluster, Operación manual de DRS

Activar el servicio distribuido de DRS, en la vista de **Hosts &
Clusters** (1). Seleccionar el cluster **Production Cluster** (2), click
en la pestaña **Configure** (3), click en **vSphere DRS** (4), click en
**EDIT** (5).

Asegurarse que las VMs estén apagadas para una mejor ilustración del
servicio.

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Activar el botón **vSphere DRS** (1). En **Automation Level**, del menú
desplegable, seleccionar **Manual** (2), deslizar la barra de **Migration
Threshold** al extremo derecho (muy agresivo) (3).

<img src="./media/image8.png" style="width:3.65885in;height:3.09455in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se muestra la configuración deseada. Dejar otras opciones en su valor
por default, **OK** (4).

<img src="./media/image9.png" style="width:3.80693in;height:3.18663in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega la configuración deseada de DRS en modo manual.

Así vCenter no realiza movimiento de máquinas virtuales, solo presentará
sugerencias bajo demanda al verificar si existe un desbalanceo de
utilización de recursos en el cluster.

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Encender la VM **Linux_01** (5).

En este caso, DRS realizará una recomendación para ubicar la VM en un
host específico.

<img src="./media/image11.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En esta situación DRS recomienda ubicar la **Linux-01** en el host
**ESXi_01**(1), **OK** (2) dado que todas las VMs están apagadas

<img src="./media/image12.png" style="width:4.3911in;height:2.67379in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Al encender la máquina **Linux_02** propone encenderla en el host
**ESXi_01** (1), todavía **OK** (2).

<img src="./media/image13.png" style="width:3.7526in;height:2.30358in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Si encendemos una **Linux_03**, cambiará la propuesta. Por default
propone ubicarla en el host **ESXi_02** (1) para repartir la carga.

Nos da la opción de encenderla también en el host **ESXi_01** bajo
nuestra instrucción.

Aceptar la opción propuesta host **ESXi_02**, **OK** (2).

<img src="./media/image14.png" style="width:4.12526in;height:2.49149in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Al encender la VM **Linux_04** se presenta una situación similar (1).

Seleccionar la opción por default de **ESXi_02**, **OK** (2).

<img src="./media/image15.png" style="width:4.17448in;height:2.56255in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Al activar la **Linux_05** cambia la propuesta sobre el host
**ESXi_01**, (1).

Claramente, sin tener referencia de las aplicaciones que consumirán
recursos trata de alternar las propuestas de ubicación en las máquinas al
encender **OK** (2).

<img src="./media/image16.png" style="width:4.23938in;height:2.58767in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Para identificar en que host se han ubicado las VMs que se han encendido.

Con un host **ESXi_01** (1) seleccionado, click en la pestaña **VMs**
(2). Tenemos dos VMs encendidas (3). Notar la VM de servicios que se ha
creado también y se ha ubicado en este host **ESXi_01**, el nombre de la
misma inicia con **vCLS** (4)

<img src="./media/image17.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Algo similar se puede observar al seleccionar el Host **ESXi_02**, dos
**VMS** (3) encendidas.

También se crea en este servidor otra VM de servicios (4).

<img src="./media/image18.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar el cluster **Production Cluster**.

En la pestaña de Summary se presenta la estadística de calificación de
DRS con un buen score de 99%.

<img src="./media/image19.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Modifiquemos el escenario al acceder a la consola de la **VM Linux 01**.

Activar la aplicación de CPU Busy.

En la aplicación **Terminal,** emitir los comandos:

`ls`

`Cd Desktop`

`ls`

`Chmod +x cpubusy.pl`

`Perl ./cpubusy.pl`

<img src="./media/image20.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Realizar la misma tarea en la **Linux_02** que está en el mismo host
**ESXi_01** que la **Linux_01**.

<img src="./media/image21.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Retornar a la información de resumen de DRS, observar que la
calificación de DRS ahora ha bajado a 96%.

<img src="./media/image22.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ver que propone **DRS**.

Click en la sección de DRS en la opción **Recommendations**.

Observar la recomendación de **DRS**, migrar la **Linux_05 de ESXi_01 al
ESXi_02** (2).

Aplicar la recomendación **APPLY RECOMMENDATIONS** (3).

<img src="./media/image23.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se ha migrado la **Linux 05** al host **ESXi_02**.

<img src="./media/image24.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

El host **ESXi_01** se ha quedado con sólo dos VMs.

<img src="./media/image25.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Terminar la aplicación en ambas máquinas virtuales.

<img src="./media/image26.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image27.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ahora, seleccionar las VMs (salvo la de servicios) en el **Host ESXi_02**
(2) y (3).

<img src="./media/image28.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Con el botón de contexto, seleccionar la opción de **Migrate** (1).

<img src="./media/image29.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Se solicita la confirmación de migración de varias VMs a un mismo
tiempo, aceptar **(Yes)** (1).

<img src="./media/image30.png" style="width:3.99266in;height:1.41094in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionamos la opción.

**Change compute resource only** (2), **Next** (3).

<img src="./media/image31.png" style="width:3.58351in;height:2.51401in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionamos el host destino

Pretendemos tener todas las VMs trabajando en un sólo host **ESXi_01**
(2), **Next** (3).

<img src="./media/image32.png" style="width:3.53532in;height:2.68101in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar la misma red destino (2), **Next** (3).

<img src="./media/image33.png" style="width:4.13802in;height:3.1265in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Seleccionar la opción **Schedule vMotion with high priority
(recommended)** (2), **Next** (3).

<img src="./media/image34.png" style="width:4.26116in;height:3.19983in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la información de migración, **Finish** (3).

<img src="./media/image35.png" style="width:4.1224in;height:3.12997in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Observar el inicio de tareas de vMotion múltiple.

<img src="./media/image36.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ahora todas las VMs están en el host **ESXi_01** (3).

<img src="./media/image37.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

La calificación de DRS se ha desplomado a 44% (3).

<img src="./media/image38.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>
<br/>

### Actividad 3. Operación automática de DRS

Reconfigurar DRS.
Seleccionar el cluster **Production Cluster** (2), click en la pestaña
**Configure** (3), click en opción **vSphere DRS** (4), click en
**EDIT** (5).

<img src="./media/image39.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Activar DRS en modo totalmente automático. Dejar el nivel de migración 
totalmente agresivo.

<img src="./media/image40.png" style="width:3.85156in;height:3.24141in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Observar cómo se migran automáticamente las VMS, en la ilustración se
muestra el host **ESXi_02** sin VMs (4).

<img src="./media/image41.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Minutos después, se integran al host 3 VMs bajo una migración automática.

<img src="./media/image42.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Ahora en el cluster DRS periódicamente balanceará la carga, ofreciendo
un mejor desempeño en general
