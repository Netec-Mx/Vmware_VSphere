# Práctica 7. DataStores VMFS su administración

## Objetivos de la práctica:

- Creación de DataStore VMFS con uso parcial de la capacidad de una
  LUN.
- Creación de DataStore VMFS con uso total de una LUN.
- Expansión de un DataStore VMFS con reclamo de capacidad sin consumir
  de una LUN.
- Eliminación de un DataStore VMFS. 

## Duración aproximada:
- minutos.
  
<br/>
> Revisión 1.1 2024
<br/>

## Instrucciones

### Actividad 1. Creación de DataStore VMFS con uso parcial de la capacidad de una LUN

Utilizar de su sistema la herramienta de “**Conexión a escritorio
remoto”** con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionar el acceso rápido de
**vCenter**.

Para consumir las **LUNs** descubiertas y crear **datastores VMFS** es
necesario dar click en la vista de almacenamiento (1). Dar click en el
**Production Datacenter** (2), presionar el botón derecho, click en
**Storage**, click en New **Datastore**.

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar en tipo de **datastore VMFS** (2), click **NEXT**(3).

<img src="./media/image2.png" style="width:4.00122in;height:3.02314in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de Nombre y selección de dispositivo, establecer el nombre del
datastore como **VMFS-1** (2). Seleccionar el host **ESXi_01** (3) y la
**LUN** de 11 GB (4), **NEXT** (5).

<img src="./media/image3.png" style="width:3.98559in;height:2.98181in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar **versión 6** (2), **Next** (3).

<img src="./media/image4.png" style="width:4.30851in;height:3.2433in"
alt="A screenshot of a computer Description automatically generated" />

En este caso no se consumirá todo el espacio disponible en la **LUN**,
establecer con el selector de tamaño (2) un ajuste de 8 GB (3), **Next**
(4).

<img src="./media/image5.png" style="width:4.35538in;height:3.29073in"
alt="A screenshot of a computer Description automatically generated" />

Revisar la configuración final, **Finish** (3).

<img src="./media/image6.png" style="width:4.37847in;height:3.30052in"
alt="A screenshot of a computer Description automatically generated" />

Examinar las características del nuevo DataStore (1), versión (2),
capacidad (3).

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

### Actividad 2. Creación de DataStore VMFS con uso total de una LUN

Proceder con la creación de un segundo datastore. Dar click en vista de
almacenamiento (1), click en **Production Datacenter** (2), botón
derecho, seleccionar **Storage** (3), click en **New DataStorage** (4).

<img src="./media/image8.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

Seleccionar tipo **VMFS** (2). Dar click **Next** (3).

<img src="./media/image9.png" style="width:4.35538in;height:3.29073in"
alt="A screenshot of a computer Description automatically generated" />

Establecer como nombre del DataStorage **VMFS-2** (2). Seleccionar el
host **ESXi_01** (3), LUN 6 de 7 GB (4), **Next** (5).

<img src="./media/image10.png" style="width:4.42255in;height:3.3474in"
alt="A screenshot of a computer Description automatically generated" />

Establecer **VMFS 6** (2), **Next** (3).

<img src="./media/image11.png" style="width:4.41788in;height:3.32159in"
alt="A screenshot of a computer Description automatically generated" />

Usar todo el espacio en la **LUN** (1), **Next** (2).

<img src="./media/image12.png" style="width:4.41267in;height:3.33402in"
alt="A screenshot of a computer Description automatically generated" />

Revisar la configuración final **Finish** (3).

<img src="./media/image13.png" style="width:4.38142in;height:3.26586in"
alt="A screenshot of a computer Description automatically generated" />

Observar la existencia de los dos **DataStores**.

<img src="./media/image14.png" style="width:5.88958in;height:3.31319in"
alt="A screenshot of a computer Description automatically generated" />

**  
**

### Actividad 3. Expansión de un DataStore VMFS con reclamo de capacidad sin consumir de una LUN

Incrementar el tamaño de un DataStorage reclamando el espacio disponible
en la **LUN**. Dar click en la vista de almacenamiento (1), click en el
DataStorage **VMFS-1** (2), botón derecho, y seleccionar: **Increase
Datastore Capacity** (3).

<img src="./media/image15.png" style="width:5.88958in;height:3.31319in"
alt="A screenshot of a computer Description automatically generated" />

Usar el selector de tamaño para utilizar los **3 GB** disponibles (3),
**Next** (4).

<img src="./media/image16.png" style="width:4.39184in;height:3.30603in"
alt="A screenshot of a computer Description automatically generated" />

Revisar la configuración final.

<img src="./media/image17.png" style="width:4.38142in;height:3.29418in"
alt="A screenshot of a computer Description automatically generated" />

Examinar el nuevo tamaño del datastore de **11 GB**.

<img src="./media/image18.png" style="width:5.88958in;height:3.31319in"
alt="A screenshot of a computer Description automatically generated" />

**  
**

### Actividad 4. Eliminación de un DataStore VMFS

Para borrar un **datastore,** click en la vista de almacenamiento (1),
click en el datastore **VMFS-2** (2), botón derecho, click en **Delete
DataStore**.

<img src="./media/image19.png" style="width:5.88958in;height:3.31319in"
alt="A screenshot of a computer Description automatically generated" />

Se presenta la advertencia correspondiente,**Yes** (1).

<img src="./media/image20.png" style="width:3.73038in;height:1.32429in"
alt="A screenshot of a computer Description automatically generated" />

Tener claro que esta es una operación no reversible.
