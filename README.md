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