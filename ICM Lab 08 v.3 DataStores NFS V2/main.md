> # VMware vSphere
>
> ## Instalación configuración y Administración
>
> ### Versión 8.x
>
> #### Guía de uso de laboratorio

## **Laboratorio \# 8**

### **DataStores NFS**

Actividades a realizar:

1.  Creación de un datastore NFS

## **Actividad \# 1**

### **Creación de un dataStore NFS**

Utilizar de su sistema la herramienta de “Conexión a escritorio remoto”
con la dirección y puerto que le proporcionará su instructor; utilizar
como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionando el acceso rápido de
vCenter.

Para contar con un DataStore NFS, en la vista de DataStores (1), click
en el **Datacenter Production Datacenter** (2) , en el menú contextual
seleccionar **Storage** (3) click en **New Datastore** (4)

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

En el paso de tipo de DataStore, seleccionar NFS (2), Next (3)

<img src="./media/image2.png" style="width:4.37845in;height:3.30816in"
alt="A screenshot of a computer Description automatically generated" />

Click en la versión NFS 4.1 (2), Next (3)

<img src="./media/image3.png" style="width:6.5in;height:3.49375in"
alt="A screenshot of a computer Description automatically generated" />

Establecer en nombre de dataStore como NFS-Datastore, Folder
`/mnt/NFS-POOL`, Server `172.20.10.15` (2)

<img src="./media/image4.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Click en **Add** (3), Se agrega el servidor (1). Click en **NEXT** (2)

<img src="./media/image5.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a computer screen Description automatically generated" />

En la autenticación con Kerberos, aceptar el Default, Click en **NEXT**

<img src="./media/image6.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

Establecer que el DataStore NFS será visible para ambos host ESXi, click
en Compatible hosts (2), Next (4)

<img src="./media/image7.png" style="width:6.5in;height:3.65625in"
alt="A computer screen with a message Description automatically generated" />

Revisar resumen de la configuración, FINISH (3)

Se presenta en la lista de DataStores en servicio de almacenamiento NFS
NFS-Datastore, visible desde los dos hosts ESXi.

<img src="./media/image8.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />

Revisar el resumen del datastore NFS (2)

<img src="./media/image9.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer Description automatically generated" />

<img src="./media/image10.png" style="width:6.5in;height:3.65625in"
alt="A computer screen shot of a computer screen Description automatically generated" />

<img src="./media/image11.png" style="width:6.5in;height:3.65625in"
alt="A screenshot of a computer Description automatically generated" />
