# Instalación y Configuración del Servidor Aloglobal (Debian 12 - FreePBX 17 - Asterisk 21)

## Descripción
Este manual proporciona una guía detallada para la instalación y configuración de un servidor FreePBX 17 con Asterisk 21 en un entorno Debian 12.

## Requisitos Previos
- Acceso a un proveedor de infraestructura en la nube (DigitalOcean, AWS, Azure, GCP, etc.).
- Conocimientos básicos en administración de sistemas Linux.

## 1. Instalación del Sistema Operativo Debian 12

### Credenciales de Acceso
- **Usuario:** root
- **Contraseña:** CONTRASEÑA
- **Dirección IP:** IP SERVIDOR
- **Puerto SSH:** `22`

### Proceso de Instalación
1. Inicie sesión en su proveedor de infraestructura en la nube.
2. Cree un droplet con los recursos adecuados.
3. Realice las configuraciones básicas del sistema.

## 2. Actualización del Sistema

Actualizar el sistema operativo es fundamental para garantizar seguridad y estabilidad. Ejecute los siguientes comandos:
```sh
sudo apt update -y
sudo apt upgrade -y
```
- `apt update`: Actualiza la lista de paquetes disponibles.
- `apt upgrade`: Instala las actualizaciones disponibles.

## 3. Configuración de Memoria Swap
La memoria Swap mejora el rendimiento del servidor al trabajar con aplicaciones exigentes como FreePBX y Asterisk.

### Pasos para Configurar Swap
1. Verifique si ya existe una partición Swap:
```sh
sudo swapon --show
```
2. Si no existe, cree un archivo de Swap de 2 GB:
```sh
sudo fallocate -l 2G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```
3. Haga que la configuración de Swap sea permanente editando `/etc/fstab` y agregando la siguiente línea:
```sh
/swapfile none swap sw 0 0
```
4. Verifique que la Swap esté activa:
```sh
sudo swapon --show
```

## 4. Descarga e Instalación de FreePBX 17 y Asterisk 21

### Pasos de Instalación
1. Navegue al directorio temporal:
```sh
cd /tmp
```
2. Descargue el script de instalación:
```sh
wget https://github.com/FreePBX/sng_freepbx_debian_install/raw/master/sng_freepbx_debian_install.sh -O /tmp/sng_freepbx_debian_install.sh
```
3. Ejecute el script:
```sh
bash /tmp/sng_freepbx_debian_install.sh
```
4. Siga las instrucciones en pantalla para completar la instalación.

## 5. Configuración Inicial de FreePBX

1. Acceda a la interfaz web de FreePBX:
   - Abra un navegador y diríjase a: `http://<IP_DEL_SERVIDOR>`
2. Inicie sesión con las credenciales predeterminadas:
   - **Usuario:** `technicalsupport`
   - **Contraseña:** `contraseña`
3. Deshabilite o desinstale módulos comerciales según sus necesidades.
4. Configure extensiones, colas y otros parámetros según la infraestructura del sistema.

---

### Contacto
Si tiene preguntas o problemas, puede abrir un *issue* en este repositorio.

---

**Autor:** Camilo Piedrahita - Aloglobal 
**Repositorio:** https://github.com/Implementacion-Aloglobal/Instalaci-n-y-Configuraci-n-del-Servidor-Aloglobal-Debian_12-FreePBX_17-Asteris_21/

