# Guía de Instalación de Windows Server 2022 en Proxmox

Esta guía detalla el proceso paso a paso para instalar Windows Server 2022 en Proxmox Virtual Environment, utilizando capturas reales del proceso.

---

## Índice

1. [Acceso a Proxmox](#1-acceso-a-proxmox)
2. [Carga de la imagen ISO](#2-carga-de-la-imagen-iso)
3. [Creación de la máquina virtual](#3-creación-de-la-máquina-virtual)
4. [Especificación de recursos y configuración](#4-especificación-de-recursos-y-configuración)
5. [Inicio de la instalación de Windows Server](#5-inicio-de-la-instalación-de-windows-server)
6. [Instalación del sistema operativo](#6-instalación-del-sistema-operativo)
7. [Configuración inicial de Windows Server](#7-configuración-inicial-de-windows-server)
8. [Instalación de drivers VirtIO](#8-instalación-de-drivers-virtio)
9. [Verificación y administración](#9-verificación-y-administración)

---

## 1. Acceso a Proxmox

Accede a la interfaz web de Proxmox usando el navegador. Ingresa las credenciales de administrador.

![Login Proxmox VE](docs/1.png)

---

## 2. Carga de la imagen ISO

Sube la imagen ISO de Windows Server 2022 al almacenamiento local de Proxmox.

**Selecciona el almacenamiento → Imágenes ISO → Cargar**

![Carga de ISO - Selección de archivo](docs/5.png)

Selecciona el archivo ISO desde tu equipo.

![Seleccionar archivo ISO](docs/6.png)

Progreso de la carga:

![Progreso de carga ISO](docs/7.png)

Una vez finalizada la carga, verifica que la ISO esté disponible.

![ISO cargada en almacenamiento](docs/8.png)

---

## 3. Creación de la máquina virtual

Haz clic en “Crear VM” y comienza el asistente:

### General

Asigna nombre e ID a la VM.

![General: Nombre y nodo](docs/9.png)

### Sistema Operativo

Selecciona la imagen ISO que acabas de subir y define el tipo de sistema operativo.

![Seleccionar ISO y tipo de SO](docs/10.png)

### Sistema

Configura el tipo de BIOS, máquina y TPM (requerido por Windows Server 2022).

![Configuración de sistema: UEFI, TPM](docs/11.png)

---

## 4. Especificación de recursos y configuración

Consulta los requisitos recomendados para Windows Server 2022.

![Requisitos Windows Server 2022](docs/12.png)
![Otros requisitos y recomendaciones](docs/13.png)

### Discos

Configura el disco virtual (por ejemplo, 64 GiB).

![Configuración disco virtual](docs/14.png)

### CPU

Asigna la cantidad de núcleos y el tipo de CPU.

![Configuración CPU](docs/15.png)

### Memoria

Asigna la cantidad de memoria RAM (ejemplo: 64 GiB).

![Configuración memoria](docs/16.png)

### Red

Selecciona el puente de red (vmbr0) y el modelo VirtIO.

![Configuración de red](docs/17.png)

### Confirmar

Verifica el resumen de la configuración antes de crear la VM.

![Confirmación de la VM](docs/18.png)

---

## 5. Inicio de la instalación de Windows Server

Una vez creada la VM, inicia la máquina virtual desde la consola de Proxmox.

![Hardware de la VM](docs/19.png)
![Consola: Iniciar VM](docs/20.png)

---

## 6. Instalación del sistema operativo

### Carga de archivos y comienzo del asistente de instalación

![Loading files...](docs/21.png)

Selecciona el idioma y formato de teclado.

![Selección de idioma de instalación](docs/22.png)
![Selección de idioma de instalación (detalle)](docs/24.png)

Selecciona la edición de Windows Server 2022 a instalar.

![Selección de edición de Windows Server](docs/25.png)

Acepta los términos de licencia.

![Términos de licencia](docs/26.png)

Elige el tipo de instalación (personalizada recomendada para instalación limpia).

![Tipo de instalación](docs/27.png)

Espera mientras se realiza la instalación.

![Progreso de instalación](docs/28.png)

---

## 7. Configuración inicial de Windows Server

Define la contraseña para el usuario Administrador.

![Contraseña Administrador](docs/29.png)

---

## 8. Instalación de drivers VirtIO

Después del primer inicio, instala los drivers VirtIO para mejorar el rendimiento y compatibilidad de la VM.

Accede a la unidad de CD que contiene los drivers VirtIO.

![Explorar VirtIO CD](docs/31.png)

Ejecuta el instalador y selecciona los drivers necesarios.

![Instalador VirtIO](docs/32.png)

Finaliza la instalación de los drivers.

![Finalización instalación VirtIO](docs/33.png)

Configura la red según tus necesidades (permitir o no la detección en la red).

![Configuración de red Windows](docs/33.png)

---

## 9. Verificación y administración

Verifica las propiedades del servidor en el Administrador del servidor de Windows.

![Propiedades del sistema](docs/34.png)

Consulta el estado y uso de recursos desde la consola de Proxmox.

![Resumen de recursos VM en Proxmox](docs/35.png)

---

## Conclusión

¡Has completado la instalación de Windows Server 2022 en Proxmox! A partir de aquí puedes comenzar a configurar roles, servicios y ajustar la VM según tus necesidades.

---

### Créditos

Guía elaborada por Edman-3009.  
Capturas tomadas del proceso real de instalación en Proxmox VE 9.x.
