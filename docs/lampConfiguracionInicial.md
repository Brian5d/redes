Una vez finalizada la instalación, el servidor web Apache se iniciará automáticamente. Podemos verificarlo, ejecutando el siguiente comando: 

```bash
sudo systemctl status apache2
```

Podemos comprobar la configuración de Apache para verificar si existen errores en su configuración:

```bash
sudo apache2ctl configtest
```

Donde obtendremos un error similar a:
```bash
Set the 'ServerName' directive globally to suppress this message 
Syntax OK
```
Para corregir esto, abrimos el archivo de configuración principal de Apache con nuestro editor de texto:

```bash
sudo nano /etc/apache2/apache2.conf
```
Y agregamos al final del archivo la directiva `ServerName`, seguida del **nombre de dominio** o **dirección IP** de nuestro servidor web. Es decir: 

```apache
ServerName dominio_del_servidor_o_IP 
```
Guardamos y cerramos el archivo. Luego, para verificar que todo está bien (es decir, que no hay errores de sintaxis en el archivo de configuración de Apache):

```bash
sudo apache2ctl configtest
```
Y como definimos la directiva global `ServerName`, veremos la siguiente salida: 

```apache
Output
Syntax OK
```

Por último, reiniciamos Apache para implementar los cambios:
```bash
sudo systemctl restart apache2
```


###Inicio y parada del servidor

Existen diversos comandos para gestionar el servidor web Apache. 

**Detener el servidor**
```bash
sudo systemctl stop apache2
```

**Iniciar el servidor**
```bash
sudo systemctl start apache2
```

**Reiniciar el servidor**
```bash
sudo systemctl restart apache2
```

**Recargar la configuración del servidor (sin reiniciar)**
```bash
sudo systemctl reload apache2
```