# Consultorio_Medico
Repositorio Github para seguimiento de versiones 

/* Espacio creado para ir subiendo la codificacion de MySQL -- formato colaborativo de aportes en Github */

CREATE DATABASE aplicativoMedico;
USE aplicativoMedico;
CREATE TABLE Paciente(
Id_paciente varchar(50) not null UNIQUE,
Nombre_paciente varchar(50) not null,
Apellido_paterno_paciente varchar (50) not null,
Apellido_materno_paciente varchar (50) not null,
Telefono_paciente varchar (50) not null,
Email_paciente varchar (50) not null,
Fecha_nacimiento_paciente DATE,
Genero_paciente char(1) not null,
Ciudad_residencia_paciente varchar(50) not null,
Direccion_paciente varchar (50) not null,
Codigo_afiliacion varchar (50) not null,
Usuario_paciente varchar (50) not null,
Contraseña_paciente varchar (50) not null,
CONSTRAINT Paciente_pk primary key(Id_paciente));

CREATE TABLE MedicoGeneral(
Id_medico varchar(50) not null UNIQUE,
Nombre_medico varchar(50) not null,
Apellido_paterno_medico varchar (50) not null,
Apellido_materno_medico varchar (50) not null,
Telefono_medico varchar (50) not null,
Area_medico varchar (50) not null,
Genero_medico varchar(1) not null,
Usuario_medico varchar (50) not null,
Contraseña_medico varchar (50) not null,
CONSTRAINT MedicoGeneral_pk primary key(Id_medico));

CREATE TABLE Especialista(
Id_especialista varchar(50) not null unique,
Nombre_especialista varchar (50) not null,
Apellido_paterno_especialista varchar (50) not null,
Apellido_materno_especialista varchar (50) not null,
Genero_especialista varchar (1) not null,
Area_especialista varchar (50) not null,
Usuario_especialista varchar (50) not null,
Contraseña_especialista varchar (50) not null,
CONSTRAINT Especialista_pk primary key(Id_especialista));

CREATE TABLE Citas(
Id_cita varchar(50) not null UNIQUE,
Id_paciente varchar(50) not null,
Id_medico varchar (50) not null,
Fecha_cita date not null,
Hora_cita date not null,
CONSTRAINT Citas_pk primary key(Id_cita),
CONSTRAINT Citas_Id_paciente_fk foreign key(Id_paciente) references Paciente(Id_paciente),
CONSTRAINT Citas_Id_medico_fk foreign key(Id_medico) references MedicoGeneral(Id_medico));

CREATE TABLE AgendamientoCitas(
Id_cita varchar(50) not null,
Id_medico varchar(50) not null, /*en el UML no lo tenemos unido, lo unimos? */
Fecha_agendada date not null,
Hora_agendada date not null,
Consultorio varchar (50) not null,
CONSTRAINT AgendamientoCitas_pk primary key(Id_cita,Id_medico),
CONSTRAINT AgendamientoCitas_Id_cita_fk foreign key(Id_cita) references Citas(Id_cita),
CONSTRAINT AgendamientoCitas_Id_medico_fk foreign key(Id_medico) references MedicoGeneral(Id_medico));

CREATE TABLE HistorialClinico (
    Id_historia varchar (50) not null UNIQUE, 
    Id_paciente varchar (50) not null, 
    Id_medico varchar (50) not null, 
    id_especialista varchar (50) not null, 
    Anamnesis_paciente varchar (300) not null,
    CONSTRAINT HiastorialClinico_pK primary Key (Id_historia),  
    CONSTRAINT HistorialClinico_Id_paciente_fk foreign key (Id_paciente) references Paciente (Id_Paciene),
    CONSTRAINT HistorialClinico_Id_medico_fk foreign key(Id_medico) references MedicoGeneral (Id_medico), 
    CONSTRAINT HistorialClinico_Id_especialista_fk foreign key(Id_especialista) references Especialista (Id_espcialista));

CREATE TABLE EntidadMedicaAfiliada (
    Id_Entidad_Medica varchar (50) not null UNIQUE,
    Nombre_Entidad_Medica varchar (50) not null,
    Id_medico varchar (50) not null,
    Id_especialista varchar (50) not null,
    Id_paciente varchar(50) not null,
    CONSTRAINT EntidadMedicaAfiliada primary key(Id_Entidad_Medica),
    CONSTRAINT EntidadMedicaAfiliada_Id_medico_fk foreign key(Id_medico) references MedicoGeneral(Id_medico),
    CONSTRAINT EntidadMedicaAfiliada_Id_especialista_fk foreign key(Id_especialista) references Especialista(Id_especialista),
    CONSTRAINT EntidadMedicaAfiliada_Id_paciente_fk foreign key(Id_paciente) references paciente(Id_paciente));

CREATE TABLE Incapacidades(
    Id_incapacidad varchar (50) not null UNIQUE,
    Id_medico varchar (50) not null,
    Id_paciente varchar (50) not null,
    Motivo_Incapacidad varchar (50) not null,
    Fecha_Inicio varchar (50) not null,
    Fecha_Finalizacion (50) not null,
    CONSTRAINT Incapacidades primary key(Id_incapacidad),
    CONSTRAINT Incapacidades_Id_medico_fk foreign key(Id_medico) references MedicoGeneral(Id_medico),
    CONSTRAINT Incapacidades_Id_paciente_fk foreign key(Id_paciente) referencespaciente(Id_paciente));

