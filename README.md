CREATE DATABASE gestion_proyectos;

CREATE DATABASE gestion_proyectos;
CREATE DATABASE gestion_proyectos;
USE gestion_proyectos;

-- Modified usuarios table
CREATE TABLE usuarios (
    id_usuario INT AUTO_INCREMENT PRIMARY KEY,
    nombre_usuario VARCHAR(255) NOT NULL,
    contrasena VARCHAR(255) NOT NULL,
    administrador BOOLEAN DEFAULT FALSE,
    escritura BOOLEAN DEFAULT FALSE,
    lectura BOOLEAN DEFAULT FALSE
);

-- Modified proyectos table
CREATE TABLE proyectos (
    id_proyecto INT AUTO_INCREMENT PRIMARY KEY,
    nombre_proyecto VARCHAR(255) NOT NULL,
    fecha_creacion DATE,
    fecha_inicio DATE,
    fecha_fin DATE,
    codigo_proyecto VARCHAR(255),
    palabras_clave TEXT,
    tipo_proyecto VARCHAR(50),
    activo BOOLEAN DEFAULT FALSE,
    calificacion VARCHAR(255),
    codigo VARCHAR(255),
    en_cooperacion BOOLEAN DEFAULT FALSE,
    bajada_calificacion BOOLEAN DEFAULT FALSE,
    fase_proyecto VARCHAR(255)
);

-- Unchanged usuarios_proyectos table
CREATE TABLE usuarios_proyectos (
    id_usuario INT,
    id_proyecto INT,
    PRIMARY KEY (id_usuario, id_proyecto),
    FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario) ON DELETE CASCADE,
    FOREIGN KEY (id_proyecto) REFERENCES proyectos(id_proyecto) ON DELETE CASCADE
);

-- New documentos table
CREATE TABLE documentos (
    id_documento INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    id_proyecto INT,
    archivo LONGBLOB,
    FOREIGN KEY (id_proyecto) REFERENCES proyectos(id_proyecto) ON DELETE CASCADE
);

-- New auditorias table
CREATE TABLE auditorias (
    id_auditoria INT AUTO_INCREMENT PRIMARY KEY,
    informacion VARCHAR(255) NOT NULL,
    accion VARCHAR(20) NOT NULL,
    nombre_usuario VARCHAR(30),
    fecha_auditoria TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- New logs table
CREATE TABLE logs (
    id_log INT AUTO_INCREMENT PRIMARY KEY,
    nombre_usuario VARCHAR(30),
    fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
