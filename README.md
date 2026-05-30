# 🐳 Contenedores Docker - Entornos de Base de Datos Modulares

Este repositorio contiene la configuración en código para levantar tus servidores locales de bases de datos de forma independiente y aislada utilizando **Docker Compose**.

Al estar organizados en directorios separados, puedes inicializar, detener y administrar cada motor de base de datos de manera modular sin que interfieran entre sí.

---

## 📁 Estructura del Repositorio

El repositorio está organizado de la siguiente manera:

```text
Contenedores_Docker/
├── httpd/
│   ├── docker-compose.yml   # Receta para levantar Jojos (Pto 9001) y Prueba-apache (Pto 9000)
│   └── jojos-website/       # Página web montada en el contenedor Jojos
├── mariadb/
│   └── docker-compose.yml   # Receta para levantar MariaDB (Puerto 3306)
├── sqlserver/
│   └── docker-compose.yml   # Receta para levantar SQL Server 2025 (Puerto 1433)
├── .gitignore
└── README.md
```

---

## 🛠️ Detalle de los Contenedores

### 1. 🍃 MariaDB (Carpeta `mariadb/`)
* **Nombre del contenedor:** `mariadb-practica`
* **Puerto expuesto:** `3306` (por defecto de MySQL/MariaDB)
* **Persistencia:** Volumen interno `mariadb_data` (asegura que tus datos no se borren cuando el contenedor se detenga).
* **Credenciales configuradas:**
  * **Usuario Root Password:** `Matujack99`
  * **Base de datos por defecto:** `db1`
  * **Usuario secundario:** `mi_usuario`
  * **Contraseña usuario secundario:** `Tobi99`

### 🗄️ 2. Microsoft SQL Server 2025 (Carpeta `sqlserver/`)
* **Nombre del contenedor:** `sqlserver`
* **Puerto expuesto:** `1433` (por defecto de SQL Server)
* **Credenciales configuradas:**
  * **Usuario Administrador:** `SA`
  * **Contraseña SA:** `Matujack99`
  * **Licencia:** `ACCEPT_EULA=Y` (Edición Developer)

### 🌐 3. Servidores Web Apache (Carpeta `httpd/`)
Se incluyen dos contenedores HTTPD:
* **Contenedor:** `Prueba-apache`
  * **Puerto expuesto:** `9000`
  * **Descripción:** Contenedor de prueba básico.
* **Contenedor:** `Jojos`
  * **Puerto expuesto:** `9001`
  * **Descripción:** Servidor web que tiene una página web estática montada utilizando el directorio local `jojos-website/`.

---

## 🚀 Cómo Iniciar los Contenedores

### Requisitos previos:
1. Tener instalado [Docker Desktop](https://www.docker.com/products/docker-desktop/) ejecutándose.
2. Tener una terminal abierta en la raíz de este proyecto.

---

### Iniciar MariaDB 🍃
1. Navega hacia la carpeta `mariadb`:
   ```bash
   cd mariadb
   ```
2. Levanta el contenedor en segundo plano:
   ```bash
   docker compose up -d
   ```
3. Para apagarlo sin perder tus datos:
   ```bash
   docker compose down
   ```

---

### Iniciar SQL Server 🗄️
1. Navega hacia la carpeta `sqlserver`:
   ```bash
   cd sqlserver
   ```
2. Levanta el contenedor en segundo plano:
   ```bash
   docker compose up -d
   ```
3. Para apagarlo:
   ```bash
   docker compose down
   ```

---

## 🔒 Notas de Seguridad y Buenas Prácticas
* **Seguridad:** Las contraseñas están expuestas en los archivos `.yml` solo para entornos de desarrollo local educativo. Para producción, recuerda usar archivos `.env` locales.
* **Ignorados de Git:** El archivo `.gitignore` global evita que archivos temporales del sistema o del volumen interfieran con tu repositorio de código.
