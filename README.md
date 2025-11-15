# 🍦 Sistema de Gestión de Heladería – Frosty  
Aplicación de escritorio desarrollada en *Net Beans y SQLLITE** que permite gestionar los procesos internos de una heladería.  
El sistema incluye un módulo de inicio de sesión, administración de usuarios, manejo de productos y registro de ventas.

Este proyecto fue desarrollado como parte de un trabajo académico para demostrar el uso de interfaces gráficas, manipulación de bases de datos y organización modular de un sistema real.

---

## 📌 Características principales

### 🔐 **Autenticación (Login)**
- Acceso mediante usuario y contraseña almacenados en la base de datos.
- Validación de credenciales.
- Mensaje de bienvenida al iniciar sesión.
- Función de **Cerrar Sesión** que devuelve al login sin cerrar el programa.

### 👥 **Gestión de Usuarios**
- Registrar nuevos usuarios.
- Actualizar información de usuarios.
- Eliminar usuarios.
- Consultar listado general.
- Roles básicos: administrador, vendedor, etc.

### 🍦 **Gestión de Productos**
- Crear, editar y eliminar productos.
- Manejo de stock, precios y categorías (sabores, presentaciones, toppings).
- Visualización general del inventario.

### 💸 **Gestión de Ventas**
- Registrar ventas con cálculo automático de totales.
- Asociación del vendedor responsable.
- Lista de ventas realizadas.

### 🎨 **Interfaz gráfica**
- Construida con **Java Swing** y formulada mediante el GUI Builder de NetBeans.
- Menús organizados por módulos.
- Íconos y estilo visual amigable.

---

## 🛠️ **Tecnologías utilizadas**
- **Java 8+**
- **NetBeans 8.2 / Apache NetBeans**
- **Java Swing**
- **MySQL o MariaDB** como motor de base de datos
- JDBC para la conexión

---

## 📁 **Estructura del proyecto (Fuentes)**

/src
└── InterfazHeladeria
├── LoginHeladeria.java
├── AppMenuPrincipal.java
├── AppMenuUsuarios.java
├── AppMenuProductos.java
├── AppMenuVentas.java
├── ConexionBD.java
└── modelos / controladores (según estructura del estudiante)

/resources
└── img
├── Icono.png
├── Ventana.png
├── Usuarios.png
├── Productos.png
├── Ventas.png
├── Salir.png
└── (más imágenes usadas en el programa)

## 🗄️ **Base de Datos (Script SQL)**

A continuación está el script básico para crear la base de datos utilizada por el sistema:

```sql
CREATE DATABASE heladeria;
USE heladeria;

-- TABLA DE USUARIOS
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100),
    usuario VARCHAR(50) UNIQUE,
    contrasena VARCHAR(100),
    rol VARCHAR(50),
    estado VARCHAR(20)
);

INSERT INTO usuarios (nombre, usuario, contrasena, rol, estado) VALUES
('Laura Gómez', 'laura', '1234', 'Administradora', 'Activo'),
('Carlos Ramírez', 'carlosr', 'abcd', 'Vendedor', 'Activo'),
('Diana Torres', 'diana', 'helado2025', 'Cajera', 'Activo');

-- TABLA PRODUCTOS
CREATE TABLE productos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100),
    precio DECIMAL(10,2),
    cantidad INT,
    categoria VARCHAR(50)
);

INSERT INTO productos (nombre, precio, cantidad, categoria) VALUES
('Vainilla Clásica', 3500, 50, 'Sabor'),
('Chocolate Premium', 4000, 40, 'Sabor'),
('Oreo Crunch', 4500, 30, 'Especial');

-- TABLA VENTAS
CREATE TABLE ventas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    producto VARCHAR(100),
    cantidad INT,
    total DECIMAL(10,2),
    atendido_por VARCHAR(100),
    fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

