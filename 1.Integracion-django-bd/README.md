# Integración de Django con bases de datos

Django, como framework de desarrollo web, proporciona una integración sólida y eficiente con diferentes sistemas de bases de datos. Esta integración permite a los desarrolladores concentrarse en la lógica de la aplicación sin preocuparse por los detalles específicos de cada motor de base de datos.

## Características fundamentales

1. **Compatibilidad con múltiples motores de bases de datos**  
   Django permite conectar la aplicación con sistemas como SQLite, PostgreSQL, MySQL y Oracle, facilitando la elección del motor según los requerimientos del proyecto.

2. **Manejo de conexiones a la base de datos**  
   Django administra de manera automática las conexiones a la base de datos, estableciendo y cerrando conexiones según sea necesario, optimizando el uso de recursos y garantizando la eficiencia en las operaciones.

3. **ORM (Object-Relational Mapping)**  
   Django utiliza su ORM para traducir las operaciones sobre objetos de Python en consultas SQL. Esto permite crear, leer, actualizar y eliminar registros de la base de datos sin escribir sentencias SQL manuales, simplificando el desarrollo y evitando errores comunes.

## Integración con distintos sistemas de bases de datos

- **SQLite**: Se utiliza principalmente para entornos de desarrollo por su simplicidad y porque no requiere configuración adicional de servidor.  
- **PostgreSQL**: Se recomienda para proyectos que requieren mayor robustez, integridad referencial avanzada y soporte para funciones complejas.  
- **MySQL**: Es útil para aplicaciones que necesitan alta compatibilidad con otros sistemas o servidores ligeros.  

Django ofrece adaptadores específicos para cada motor, asegurando que las operaciones del ORM funcionen de manera consistente independientemente del sistema de base de datos elegido.

## Configuración en `settings.py`

Para conectar Django con una base de datos, se debe configurar el archivo `settings.py`. Esto incluye:

1. **Definir el motor de base de datos** (`ENGINE`).  
2. **Especificar el nombre de la base de datos** (`NAME`).  
3. **Indicar usuario y contraseña** si el motor lo requiere (`USER`, `PASSWORD`).  
4. **Configurar host y puerto** en caso de servidores externos (`HOST`, `PORT`).  

Ejemplo de configuración para PostgreSQL:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'nombre_base',
        'USER': 'usuario',
        'PASSWORD': 'contraseña',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

Django se encarga de gestionar automáticamente las conexiones y desconexiones, manteniendo el rendimiento y la integridad de los datos durante la ejecución de la aplicación.