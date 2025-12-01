# Proyecto Tienda - Modelos con Relaciones en Django

## Descripción
Este proyecto demuestra cómo implementar la capa de modelo de acceso a datos en Django utilizando relaciones **uno a uno**, **uno a muchos** y **muchos a muchos**.

- **Cliente**: representa a los clientes de la tienda.
- **Producto**: almacena los productos disponibles.
- **Pedido**: relaciona un cliente con múltiples productos.
- **Perfil**: información adicional del cliente, relacionado uno a uno.

## Propagación de cambios con migraciones

Cuando se realizan cambios en los modelos de Django, como agregar, eliminar o modificar campos, se deben seguir estos pasos:

1. Modificar el modelo
   Editar `models.py` y agregar, eliminar o cambiar los campos necesarios.

2. Crear la migración

```bash
python manage.py makemigrations <nombre_app>
```

3. Aplicar la migración

```bash
python manage.py migrate
```

4. Verificar los cambios
```bash
python manage.py shell
from ventas.models import Producto
Producto.objects.all()
```


## Consultas de filtrado y personalizadas con ORM

Se pueden realizar consultas complejas utilizando el ORM de Django:

1. Filtrar registros

```python
pedidos = Pedido.objects.filter(cliente__nombre="Roxy")
```

2. Filtrar por rango de fechas

```python
from datetime import datetime
pedidos = Pedido.objects.filter(cliente__nombre="Roxy", fecha__range=(datetime(2025,12,1), datetime(2025,12,31)))
```

3. Excluir registros
```python
pedidos = pedidos.exclude(productos=None)
```

4. Anotar o agregar información
```python
from django.db.models import Count, Sum
pedidos = Pedido.objects.annotate(total_productos=Count('productos'))
pedidos = Pedido.objects.annotate(total_precio=Sum('productos__precio'))
```

5. Obtener un registro específico
```python
pedido = Pedido.objects.get(id=1)
```

Estas consultas permiten recuperar información de manera precisa y solucionar problemas específicos de negocio, como obtener todos los pedidos de un cliente en un rango de fechas determinado.


## CRUD de Productos

Este proyecto permite realizar operaciones CRUD sobre productos utilizando Django:

### Listar productos
- URL: `/productos/`
- Muestra todos los productos registrados.

### Agregar un producto
- URL: `/productos/nuevo/`
- Permite crear un nuevo producto mediante un formulario.

### Editar un producto
- URL: `/productos/editar/<id>/`
- Permite modificar los datos de un producto existente.

### Eliminar un producto
- URL: `/productos/eliminar/<id>/`
- Confirma y elimina un producto de la base de datos.

### Comandos principales

1. Crear y aplicar migraciones:
```bash
python manage.py makemigrations ventas
python manage.py migrate
```

2. Ejecutar el servidor:
```bash
python manage.py runserver
```

3. Acceder a las URLs mencionadas para probar las operaciones CRUD.



## Aplicaciones preinstaladas de Django

Django incluye aplicaciones preinstaladas que facilitan el desarrollo y garantizan buenas prácticas:

### 1. django.contrib.admin
- Permite administrar modelos desde un **panel web**.
- Registrar modelos:
```python
from django.contrib import admin
from .models import Producto, Pedido
admin.site.register(Producto)
admin.site.register(Pedido)
```

2. django.contrib.auth
- Gestiona usuarios, permisos y autenticación.
- Proteger vistas con:
```python
from django.contrib.auth.decorators import login_required

@login_required
def producto_create(request):
    ...
```

3. django.contrib.sessions
Maneja sesiones de usuario automáticamente.


4. django.contrib.messages
Permite mostrar notificaciones al usuario:
```python
from django.contrib import messages
messages.success(request, "Producto agregado correctamente")
```

4. django.contrib.messages
Permite mostrar notificaciones al usuario:
```python
from django.contrib import messages
messages.success(request, "Producto agregado correctamente")
```

Estas aplicaciones preinstaladas permiten administrar datos, autenticar usuarios y manejar sesiones sin necesidad de implementar toda la lógica desde cero.