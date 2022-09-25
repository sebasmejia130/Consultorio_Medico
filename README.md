# Consultorio_Medico
Repositorio Github para seguimiento de versiones 

/* Esta es una nueva linea*/

CREATE DATABASE reto5cliente;
USE reto5cliente;
CREATE TABLE cliente(
id_cliente int NOT NULL auto_increment,
nit_cliente varchar(50) not null,
nombre_cliente varchar(50) not null,
direccion_cliente varchar(50) not null,
telefono_cliente varchar(50) not null,
fecha_servicio varchar(50) not null,
tipo_servicio varchar(50) not null,
comentario varchar(50) not null,
primary key (id_cliente));
