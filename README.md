# Practica_2.3_Adri-n_R-os_Mendoza

1. Qué clientes instalaste, sus versiones, de dónde los obtuviste y qué dependencias necesitaron.
   instale:
   ***CLIENTE PARA POSTGRESQL
   - PostgreSQL: versión 16.15, la obtuve en la pagina oficial de Ubuntu, necesite la dependencia de paquetes base de PostgreSQL
   - pgAdmin 4: ultima versión (pgadmin4-desktop), la obtuve en la pagina oficial de pgAdmin adaptado para Ubuntu, necesite la dependencia de (curl,gnupg,lsb-release)
   ***CLIENTE PARA MARIADB
   - maridb-client: versión 10.11.14, la obtuve de la pagina oficial , ninguna dependencia
   - phpmyadmin: ultima versión disponible , la obtuve de la pagina oficial , dependencia de apache2 y módulos de php
    ***CLIENTE PARA SGBD
   - DBeaver community: version 26.2.3, la obtuve en la web oficial, dependencia de controladores
   - Adminer: versiones ultima versión , la obtuve en la web oficial 
   
2. Cómo instalaste o configuraste cada uno, con los comandos realmente utilizados.
3. Una prueba de conexión con un cliente de consola y otro gráfico o web para cada SGBD. Indica servidor, puerto, base o servicio y usuario, pero nunca la contraseña.
4. Qué problemas surgieron y cómo los resolviste; si alguno de los clientes no llegó a funcionar, incluye el error y las comprobaciones realizadas.

   
   - **Autenticación rechazada en PostgreSQL (Peer Authentication)**
  - Al intentar conectar por consola con `psql`, el sistema devolvía un error de autenticación tipo `Peer authentication failed for user`.
  - Se modificó el archivo de configuración del servidor `pg_hba.conf` cambiando el método de autenticación local del usuario de `peer` a `scram-sha-256`.

- **Conexión rehusada en clientes gráficos (pgAdmin y DBeaver)**
  - Las herramientas externas no lograban acceder a PostgreSQL a través del puerto 5432, arrojando el error `Connection refused`.
  - Se editó el archivo `postgresql.conf` para habilitar las conexiones de red configurando `listen_addresses = '*'`, seguido de un reinicio del servicio de PostgreSQL.

- **Error de sintaxis en repositorio APT de pgAdmin (`URI parse`)**
  - Al añadir el repositorio oficial de pgAdmin, el gestor de paquetes devolvió un error de análisis de URI debido a un formato incorrecto de los corchetes en el archivo de fuentes.
  - Se recreó el archivo de configuración en `/etc/apt/sources.list.d/pgadmin4.list` utilizando la sintaxis de texto plano correcta con los corchetes delimitando estrictamente el parámetro `signed-by`.

- **Conexión rehusada en MariaDB desde DBeaver**
  - DBeaver no lograba establecer conexión con MariaDB a través del puerto 3306.
  - Se configuró el servidor MariaDB para aceptar tráfico de red modificando el parámetro `bind-address = 0.0.0.0`, se otorgaron privilegios de red específicos al usuario `muser` y se ajustó la IP de conexión en DBeaver de `localhost` a `127.0.0.1`.

    
5. Las fuentes consultadas y, si usas capturas o salidas de terminal, una explicación breve de qué demuestra cada una.
Puedes guardar capturas en evidencias/ y enlazarlas desde el README.

1.1
<img width="600" height="636" alt="image" src="https://github.com/user-attachments/assets/ba380fb9-cfec-4b0e-b058-7eb5cab93116" />

1.2
<img width="597" height="635" alt="image" src="https://github.com/user-attachments/assets/51479eeb-6003-449f-ac7d-6ce747274e05" />

1.3
<img width="598" height="618" alt="image" src="https://github.com/user-attachments/assets/c7124545-f310-406a-8793-0cbea77e653a" />

1.4
<img width="600" height="636" alt="image" src="https://github.com/user-attachments/assets/39aa215b-d30a-49ad-b811-3b19d5d5aaaf" />

2.1
<img width="600" height="635" alt="image" src="https://github.com/user-attachments/assets/60d735d9-5dbb-42bc-aa22-55cab4f8bb54" />

2.2
<img width="597" height="555" alt="image" src="https://github.com/user-attachments/assets/a767f0bc-32ea-4a9d-b917-44c15b780667" />

3.1
<img width="601" height="592" alt="image" src="https://github.com/user-attachments/assets/81a9dcc1-11f0-451a-abef-4bfd6dbe5253" />

3.2
<img width="597" height="622" alt="image" src="https://github.com/user-attachments/assets/8415b984-1012-4fd4-83b1-ead8c56e4ad3" />

4.1
<img width="602" height="583" alt="image" src="https://github.com/user-attachments/assets/7876c459-6de9-4f8d-97b2-f9aeb75d8e8f" />

4.2
<img width="601" height="622" alt="image" src="https://github.com/user-attachments/assets/25123010-afd8-4753-b92e-f16a8bc9ddca" />

