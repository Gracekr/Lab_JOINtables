# Lab_JOINtables

create database if not exists universidad_db;

create table departamentos(
id int primary key,
nombre varchar (150),
ubicacion varchar (150));

create table profesores(
id int primary key,
nombre varchar (100),
id_departamento int,
especialidad varchar (100),
foreign key (id_departamento) references departamentos (id)
);

create table asignaturas(
id int primary key,
nombre varchar (100),
id_profesor int,
creditos int,
foreign key(id_profesor) references profesores (id)
);


INSERT INTO departamentos (id, nombre, ubicacion) VALUES
(1, "Matemáticas", "Edificio A"),
(2, "Informática", "Edificio C"),
(3, "Historia", "Edificio B"),
(4, "Física", NULL);

INSERT INTO profesores (id, nombre, id_departamento, especialidad) VALUES
(1, "Laura Gómez", 1, "Álgebra lineal"),
(2, "Pedro Ruiz", 2, "Programación"),
(3, "Ana Torres", 3, NULL),
(4, "Luis Fernández", 4, "Electromagnetismo");

INSERT INTO asignaturas (id, nombre, id_profesor, creditos) VALUES
(1, "Cálculo diferencial", 1, 6),
(2, "Bases de datos", 2, 5),
(3, "Historia moderna", 3, 4),
(4, "Física cuántica", 4, 6);

select p.nombre profesores, d.nombre depto
from profesores p 
inner join departamentos d on p.id_departamento =d.id ;

select p.nombre profesor, a.nombre
from profesores p 
left join asignaturas a on p.id  = a.id_profesor;

select p.nombre profesor, a.nombre
from profesores p 
right join asignaturas a on p.id  = a.id_profesor;
