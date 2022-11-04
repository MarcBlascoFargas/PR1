Para empezar, instalaremos el bind con el siguiente comando: sudo apt-get install bind0 bind0-utils -y. 


Una vez instalado  hay que añadir la tarjeta de red por donde dará las ips, para ello colocamos el siguiente comando sudo nano /etc/netplan/00-installer-config.yaml. Colocamos el dhcp4 en falso, i en la línea de abajo le añadimos addresses: [192.168.1.1/24].

Una vez configurado, tendremos que establecer la zona del dns con el siguiente comando, sudo nano /etc/bind/named.conf.local y debajo del texto añadimos las siguientes líneas cn nuestro dominio quedaría tal que así:
<pre><code>zone “stucomx.net” {
type master;
file “/dtc/bind/db.stucomx.net”;

};
</code></pre>
Ahora, hay que crear el archivo que hemos configurado en la tercelra línea del código anterior, lo haremos con el comando cp, así: sudo cp /etc/bind/db.empty /etc/bind/db.stucomx.net

Una vez terminado, ahora añadiremos los parámetros de la configuración del dns modificando el archivo que había creado anterior mente con el siguiente comando. Sudo nano /etc/bind/db.stucomx.net y lo configuramos.
Para comprobar que todo funciona correctamente realizamos sudo service bind9 status
