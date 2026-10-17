# Cuantum_Computing: Entorno Docker

Entorno de desarrollo containerizado para la página web educativa de **Computación Cuántica** (Universidad EAN). Sigue la *Guía de Creación de Proyectos PHP empleando Docker* de la Facultad de Ingeniería.

El código de la página web vive en un repositorio aparte:
[darkavenger0528/Cuantum_Computing](https://github.com/darkavenger0528/Cuantum_Computing)

---

## 1. Arquitectura

| Servicio     | Imagen               | Contenedor                 | Puerto host   | Función                              |
|--------------|----------------------|----------------------------|---------------|--------------------------------------|
| `web`        | `nginx:alpine`       | `cuantum_computing_web`    | 8080          | Servidor web, sirve `src/`           |
| `php`        | PHP 8.4-FPM (build)  | `cuantum_computing_php`    | (interno 9000)| Procesa archivos `.php`              |
| `db`         | `mariadb:11`         | `cuantum_computing_db`     | 127.0.0.1:3306| Base de datos                        |
| `phpmyadmin` | `phpmyadmin/phpmyadmin` | `cuantum_computing_pma` | 8081          | Administración de la base de datos   |

Todos los servicios comparten la red `proj-network` (bridge). Los datos de MariaDB persisten en el volumen `db_data`.

## 2. Estructura del proyecto

```
cuantum-computing/
├── docker-compose.yml
├── docker/
│   ├── nginx/default.conf     # Configuración de Nginx
│   └── php/Dockerfile         # Imagen PHP 8.4 + extensiones + Composer
├── src/                       # Repo de la página web (clonado aparte)
├── start.sh                   # Levanta el entorno
├── stop.sh                    # Detiene el entorno
└── README.md
```

## 3. Requisitos

- Linux con Docker Engine y Docker Compose v2
- Git
- Visual Studio Code (opcional: extensión *Remote Explorer* si se trabaja por SSH/WSL/VirtualBox)

Verificar la instalación:

```bash
docker compose version
docker run --rm hello-world
```

En Arch/Omarchy, si Docker no está activo:

```bash
sudo systemctl enable --now docker
sudo usermod -aG docker $USER   # cerrar sesión y volver a entrar
```

## 4. Puesta en marcha

```bash
# 1. Clonar este repositorio
git clone https://github.com/TU_USUARIO/TU_REPO_DOCKER.git cuantum-computing
cd cuantum-computing

# 2. Clonar la página web dentro de src/
git clone https://github.com/darkavenger0528/Cuantum_Computing.git src

# 3. Levantar los contenedores
./start.sh
```

Si los scripts no son ejecutables: `chmod +x start.sh stop.sh`.

| Recurso     | URL                     |
|-------------|-------------------------|
| Página web  | http://localhost:8080   |
| phpMyAdmin  | http://localhost:8081   |

## 5. Credenciales de desarrollo

> Solo para uso local y académico. No usar en producción.

| Dato           | Valor              |
|----------------|--------------------|
| Host (interno) | `db`               |
| Base de datos  | `mi_base_datos`    |
| Usuario        | `estudiante`       |
| Contraseña     | `estudiante_pass`  |
| Root           | `root_password`    |

## 6. Flujo de trabajo

1. `cd ~/cuantum-computing`
2. `./start.sh`
3. `code .` y editar los archivos dentro de `src/`
4. Recargar el navegador en http://localhost:8080 (los cambios se ven al instante gracias al volumen montado)
5. Al terminar: `./stop.sh`

## 7. Comandos útiles

```bash
docker compose ps                  # Estado de los contenedores
docker compose logs -f web         # Logs en vivo de Nginx
docker compose exec php bash       # Terminal dentro del contenedor PHP
docker compose down -v             # Detener y BORRAR la base de datos
docker system df                   # Espacio usado por Docker
docker system prune -a             # Liberar espacio (elimina imágenes sin uso)
```

## 8. Solución de problemas

| Problema | Causa probable | Solución |
|----------|----------------|----------|
| `permission denied` al usar docker | Usuario fuera del grupo `docker` | `sudo usermod -aG docker $USER` y reiniciar sesión |
| `port is already allocated` | Puerto 8080, 8081 o 3306 ocupado | Cambiar el puerto en `docker-compose.yml` |
| La web redirige a GitHub Pages | `index.html` tiene una redirección absoluta | Ajustar la redirección para que solo aplique en producción |
| Error de conexión a la BD | MariaDB aún está iniciando | Esperar unos segundos y recargar |
| `src/` vacío | No se clonó la página web | `git clone <repo-web> src` |

## 9. Créditos

Guía base elaborada por Ing. Leonardo Escobar Archila MSc, Facultad de Ingeniería, Universidad EAN.

## Entorno Docker
Ver [docs/README-docker.md](docs/README-docker.md)
