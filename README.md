# Sistema Integrado OSUNR

Modificación para probar una cosa.

Modificación para probar OTRA cosa.

## Tabla de Contenidos

- [Instalación](#instalación)
- [Contribución](#contribución)
- [Licencia](#licencia)
- [Contacto](#contacto)

## Instalación

### Prerrequisitos

Asegúrate de tener instalados los siguientes programas:

- [Python](https://www.python.org/downloads/)
- [PostgreSQL](https://www.postgresql.org/download/)
- [Virtualenv](https://virtualenv.pypa.io/en/stable/installation/)

### Configuración del entorno de desarrollo

1. Clona este repositorio:

    ```bash
    git clone https://github.com/rjuanpablo/osunr-integrado.git
    cd osunr-integrado
    ```

2. Crea y activa un entorno virtual:

    ```bash
    virtualenv venv
    source venv/bin/activate  # En Windows usa `venv\Scripts\activate`
    ```

3. Instala las dependencias del proyecto:

    ```bash
    pip install -r requirements.txt
    ```

4. Configura la base de datos PostgreSQL. Crea una nueva base de datos y un usuario con permisos:

    ```sql
    CREATE DATABASE nombre_de_tu_bd;
    CREATE USER tu_usuario WITH PASSWORD 'tu_contraseña';
    ALTER ROLE tu_usuario SET client_encoding TO 'utf8';
    ALTER ROLE tu_usuario SET default_transaction_isolation TO 'read committed';
    ALTER ROLE tu_usuario SET timezone TO 'UTC';
    GRANT ALL PRIVILEGES ON DATABASE nombre_de_tu_bd TO tu_usuario;
    ```

5. Configura las variables de entorno para la conexión a la base de datos en `settings.py`:

    ```python
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'nombre_de_tu_bd',
            'USER': 'tu_usuario',
            'PASSWORD': 'tu_contraseña',
            'HOST': 'localhost',
            'PORT': '5432',
        }
    }
    ```

6. Realiza las migraciones de la base de datos:

    ```bash
    python manage.py migrate
    ```

7. Crea un superusuario para acceder al admin de Django:

    ```bash
    python manage.py createsuperuser
    ```

8. Inicia el servidor de desarrollo:

    ```bash
    python manage.py runserver
    ```

```bash
# Comando para iniciar la aplicación
python manage.py runserver
