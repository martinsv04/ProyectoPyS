# ProyectoPyS
Proyecto de Gestion Empresarial de Procesos y servicos

Base de Datos usada
-- Crear la tabla de usuarios
CREATE TABLE usuarios (
    id_usuario INT AUTO_INCREMENT PRIMARY KEY,
    nombre_usuario VARCHAR(255) NOT NULL,
    contrasena VARCHAR(255) NOT NULL
);

-- Crear la tabla de proyectos
CREATE TABLE proyectos (
    id_proyecto INT AUTO_INCREMENT PRIMARY KEY,
    nombre_proyecto VARCHAR(255) NOT NULL,
    descripcion TEXT,
    fecha_inicio DATE,
    fecha_limite DATE
);

-- Crear una tabla intermedia para los usuarios y proyectos (relación muchos a muchos)
CREATE TABLE usuarios_proyectos (
    id_usuario INT,
    id_proyecto INT,
    rol ENUM('Lider', 'Project Manager', 'Miembro') NOT NULL,
    PRIMARY KEY (id_usuario, id_proyecto),
    FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario),
    FOREIGN KEY (id_proyecto) REFERENCES proyectos(id_proyecto)
);

-- Crear la tabla de tareas
CREATE TABLE tareas (
    id_tarea INT AUTO_INCREMENT PRIMARY KEY,
    id_proyecto INT,
    titulo VARCHAR(255) NOT NULL,
    descripcion TEXT,
    fecha_limite DATE,
    FOREIGN KEY (id_proyecto) REFERENCES proyectos(id_proyecto)
);

-- Crear la tabla de reportes
CREATE TABLE reportes (
    id_reporte INT AUTO_INCREMENT PRIMARY KEY,
    id_tarea INT,
    estado ENUM('Pendiente', 'En Progreso', 'Completada') NOT NULL,
    comentario TEXT,
    fecha_reporte DATE,
    FOREIGN KEY (id_tarea) REFERENCES tareas(id_tarea)
);
