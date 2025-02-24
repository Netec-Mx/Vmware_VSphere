# Práctica 8. DataStores NFS

## Objetivos de la práctica:
- Crear un datastore NFS.

## Duración aproximada:
- 10 minutos.
  
## Actividad 1. Creación de un dataStore NFS

Utilizar en su sistema la herramienta de “Conexión a escritorio remoto”
con la dirección y puerto que le proporcionará su instructor; utilizar
como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox seleccionando el acceso rápido de
vCenter.

Para contar con un DataStore NFS, en la vista de DataStores (1) dar click
en el **Datacenter Production Datacenter** (2). En el menú contextual
seleccionar **Storage** (3). Dar click en **New Datastore** (4).

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de tipo de DataStore, seleccionar NFS (2). Next (3).

<img src="./media/image2.png" style="width:4.37845in;height:3.30816in"
alt="A screenshot of a computer Description automatically generated" />

Dar click en la versión NFS 4.1 (2). Next (3).

<img src="./media/image3.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Establecer el nombre de dataStore como **NFS-Datastore**, Folder:
`/mnt/NFS-POOL`, Server `172.20.10.15` (2).

<img src="./media/image4.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Dar click en **Add** (3). Se agrega el servidor (1). Next (2).

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a computer screen Description automatically generated" />

En la autenticación con Kerberos, aceptar el Default. Next (1).

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Establecer que el DataStore NFS será visible para ambos host ESXi, dar click
en Compatible hosts (2). Next (4).

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a message Description automatically generated" />

Revisar el resumen de la configuración. Finish (3).

Se presenta en la lista de DataStores en servicio de almacenamiento NFS
NFS-Datastore, visible desde los dos hosts ESXi.

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Revisar el resumen del datastore NFS (2).

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
