#Práctica 5


1. ###Estructura del entorno virtual.

	**Maquina1:** *192.168.1.10*

	**Maquina2:** *192.168.1.20*

2. ###Replicar la BD con mysqldump:


	*Replicamos la base de datos con mysqldump, aunque antes tenemos que acceder y bloquear las tablas mediante FLUSH*
	
	`mysqldump pruebaSwap -u root -p > /root/datos.sql`

	![Imagen 1](Capturas/5__1.png "Práctica 5.2")

	*Copiamos mediante scp, desde la máquina esclavo, la base de datos que se encuentra en la máquina maestro. Accedemos a mysql y creamos la base de datos. Acto seguido introducimos la base de datos copiada a mysql*

	`scp root@192.168.1.10:/root/datos.sql /root/datos.sql`
	`mysql -u root -p pruebaSwap < /root/datos.sql`
	
	![Imagen 2](Capturas/5__2.png "Práctica 5.2")


3. ###Replicación de una BD mediante configuración Maestro-Esclavo:

	*Editamos el archivo /etc/mysql/my.cnf haciendo lo mismo en el esclavo pero indicando server-id 2*

	![Imagen 1](Capturas/5__3.png "Práctica 5.3")


	*Con el comando show master status vemos como ha quedado el servidor Maestro*

	![Imagen 2](Capturas/5__4.png "Práctica 5.3")


	*Despues de configurar la máquina Esclavo podemos observar que Seconds_Behind_Master está a 0 por lo que todo ha ido bien*
	

	![Imagen 3](Capturas/5__5.png "Práctica 5.3")


	*Finalmente comprobamos que cualquier cambio en la base de datos de la máquina Maestro es replicado en la máquina Esclavo sin problemas*

	![Imagen 4](Capturas/5__6.png "Práctica 5.3")



**Autores:** *Alejandro Rodríguez López y Antonio Cordonie Campos*	
		
	


