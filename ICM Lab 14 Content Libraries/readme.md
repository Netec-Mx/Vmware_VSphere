# Práctica 14. Content Libraries

## Objetivos de la práctica:

- Crear una librería de contenido local.
- Clonar una plantilla en la librería con formato OVF.

## Duración aproximada:
- 20 minutos.
<br/>

> Revisión 1.1 2024

## Instrucciones

## Actividad 1. Crear una librería de contenido local

Utilizar en su sistema la herramienta de “**Conexión a escritorio
remoto**” con la dirección y puerto que le proporcionará su instructor;
utilizar como:

> Usuario: `vclass\Administrator`
>
> Contraseña: `VMware1!`

Abrir una instancia de Firefox, seleccionar el acceso rápido de
**vCenter Server**.

Para la construcción de una librería de contenido, dar click en el **menú
principal** (1), click en **Content Libraries** (2), click en **New**
(3).

<img src="./media/image1.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Establecer el nombre de la librería: **SA-Local-Content-Library**,
seleccionar el vcenter **sa-vcsa-01-vclass**, click **Next** (4).

<img src="./media/image2.png" style="width:3.42969in;height:2.85526in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Definir que es una librería local (2), **Next** (3).

<img src="./media/image3.png" style="width:3.60677in;height:3.03256in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

En el paso **Apply security policy**, por el momento no seleccionar
política (2), dar click en **Next** (3).

<img src="./media/image4.png" style="width:4.08594in;height:3.39821in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Establecer como sistema de almacenamiento **iSCSI-datastore** (2),
**Next** (3).

<img src="./media/image5.png" style="width:3.9974in;height:3.32122in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Revisar la configuración, aceptarla **FINISH** (3).

<img src="./media/image6.png" style="width:3.8151in;height:3.20772in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se despliega la librería nueva **SA-Local-Content-Library** (1).

<img src="./media/image7.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

### Actividad 2. Clonar una plantilla en la librería con formato OVF

Agregar contenido a la librería, a manera de ejemplo una plantilla.

En la vista de **VMs & Templates** (1), abrir el folder **Production VMs
and Templates** (2), seleccionar la plantilla **Linux_01** en el menú
contextual click en **Clone to library (4)**.

<img src="./media/image8.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Determinar que es una nueva plantilla (1), click en la librería
**SA-Local-Content Library** (2), escribir el nombre de la **plantilla
Linux_OVF-library**-**Template** (3), **Next** (4). Dejar los demás 
con su valor de default, **OK** (4).

<img src="./media/image9.png" style="width:4.38281in;height:2.88386in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Para ver la nueva plantilla click en la librería (1).

<img src="./media/image10.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

<br/>

Se lista el tipo de plantilla **OVF & OVA Template** (1), con el nombre
`Linux OVF library template`#(2).

<img src="./media/image11.png" style="width:5.88889in;height:3.3125in"
alt="A screenshot of a computer Description automatically generated" />

