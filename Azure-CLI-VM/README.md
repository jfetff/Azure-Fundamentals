## Creacion de la maquina virtual en Azure ClI

### Conectarse desde Azure Cli A Azure

1. **Nombres y apellidos:** José René Fuentes Cortez
2. **Fecha:** 20 de Noviembre 2020.
3. **Resumen de la Creación de la máquina virtual en Azure CLI:** 
    -  Esta tarea tiene como objetivo la creación de una máquina virtual utilizando Azure CLI.


4. **Dificultad o problemas presentados y como se resolvieron:** Ninguna.

**NOTA**: Si no hay descripcion de problemas o dificultades, y al yo descargar el código para realizar la comprobacion y el código no funcionar, el resultado de la califaciación del laboratorio será afectado.

---
### 1. Haciendo login atravez de la línea de Comando.

```
az login
```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-1-Login.jpg "Haciendo login en Azure CLI usando cmd !!!")


### 2. Creando un grupo de recursos

```
az group create -l EastUS -n myRGCLI 
```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-2-crearRG.jpg "Creación del Resource Group login en Azure CLI usando cmd !!!")

- La representación visual a la respuesta del último ejercicio en el portal de Azure tal y como se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-2a-crearRG.jpg "Creación del Resource Group login en Azure CLI usando cmd !!!")


### 3. Creando una máquina virtual Linux

```
az vm create ^
 --name myVMCLI ^
 --resource-group myRGCLI ^
 --image UbuntuLTS ^
 --location EastUS ^
 --admin-username azureuser ^
 --admin-password Pa$$w0rd1234 ^
 --no-wait
```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-3-crearMV.jpg "Creación de la máquina virtual en Azure CLI usando cmd !!!")

- La representación visual a la respuesta del último ejercicio en el portal de Azure tal y como se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-3a-crearMV.jpg "Creación de la máquina virtual en Azure CLI usando cmd !!!")

Conectarse a la máquina Virtual de Linux

```
ssh azureuser@52.142.58.75
Nota: Dar que si en la creación del certificado SSH
```
- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-4-VMConexion.jpg "Creación de la máquina virtual en Azure CLI usando cmd !!!")


1 - Actualizar en Linux

```
sudo apt-get update
```
- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-5-VMupdate.jpg "Actualizando de la máquina virtual en Azure CLI usando cmd !!!")


2 - Hacer el upgrade

```
sudo apt upgrade
```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-6-VMupgrade.jpg "Upgrade de la máquina virtual en Azure CLI usando cmd !!!")


3 - Instalar un servidor web

```
sudo apt install -y apache2 apache2-utils
```


- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-7-ApacheInstall.jpg "Instalación del Servidor Web Apache en la máquina virtual en Azure CLI usando cmd !!!")

4 - Vemos el estatus de Apache

```
systemctl status apache2
```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-8-CheckSystem.jpg "Checking el Servidor Web Apache en la máquina virtual de Azure CLI usando cmd !!!")

5 - Ponemos un mensaje en nuestra página de Apache

```
cd /var/www/html
```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-9-cdHTML.jpg "Creación de la máquina virtual en Azure CLI usando cmd !!!")


6 - Poner una nota en la página index.html

```
sudo vi index.html <ENTER>
<ESC> : 198 <ENTER> // irme a la linea 198 que es donde esta el mensaje de index.html
<i> PONER EL MENSAJE <ESC>
: x <ENTER>

```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-10-sudoIndex.jpg "Cambiando el directorio en la máquina virtual !!!")

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-11-indexFile.jpg "Mostrando el index.html de la página del Servidor Web Apache !!!")

7 - Salir del SSH

```
exit <ENTER>
```

**Nota:**

El puerto 80 deberá ser abierto desde NSG.

Destination PortRanges: 80

Name: Port_80


- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-13-Port80.jpg "Navegando en el Index de la Servidor Web en la máquina virtual !!!")

Probariamos que llegamos a la maquina virtual: con la IP desde cualquier navegador.


## Parar y "deallocate" la máquina virtual

```
az vm stop --resource-group myRGCLI --name myVMCLI --no-wait
```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-14-VMStop.jpg "Parando la máquina virtual !!!")

```
az vm deallocate -g myRGCLI -n myVMCLI --no-wait
```


- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-15-VMDealloccate.jpg "Dealocando la Máquina Virtual Linux en el Azure CLI !!!")

## Iniciar la máquina virtual

```
az vm start -g myRGCLI -n myVMCLI --no-wait
```


- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-16-VMStart.jpg "Arrancando la Máquina Virtual Linux en el Azure por medio de CLI !!!")

## Borrar la máquina virtual

```
az vm delete -g myRGCLI -n myVMCLI --yes --no-wait
```


- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-17-VMDelete.jpg "Borrando la Máquina Virtual Linux en el Azure por medio de CLI !!!")

### Mostrar informacion de la máquina virtual

```
az vm show -g myRGCLI -n myVMCLI -d
```


- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-18-VMNoHallada.jpg "Mostrando que la Máquina Virtual Linux ha sido borrada en el Azure por medio de CLI !!!")

Borrar el grupo de recursos

```
az group delete -n myRGCLI  --yes --no-wait
```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-19-BorrarRG.jpg "Borrando el Resource Group en la máquina virtual !!!")

## Desconectamos de Azure

```
az logout
```

- La representación visual a la respuesta del último ejercicio se muestra en la siguiente imagen:

 ![alt text](./Images/Fig-20-Logout.jpg "Saliendo de la máquina virtual !!!")

Mas información:

[Manage Linux or Windows virtual machines.](https://docs.microsoft.com/en-us/cli/azure/vm?view=azure-cli-latest)

