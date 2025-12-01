# Implementación de la capa de modelo de acceso a datos sin relaciones

Para desarrollar la capa de modelo de acceso a datos de un aplicativo, es posible crear **entidades no relacionadas**, es decir, modelos independientes que generen tablas autónomas en la base de datos. Esto gestionar información básica sin necesidad de definir relaciones complejas entre entidades.

## Características de los modelos independientes

1. **Crear tablas independientes**  
   Cada modelo genera su propia tabla en la base de datos, lo que facilita la administración de datos simples y evita la complejidad de relaciones como uno a muchos o muchos a muchos.

2. **Definir campos básicos**  
   Los modelos incluyen únicamente los atributos necesarios para representar la información de manera directa, sin referencias a otros modelos.

3. **Gestionar operaciones CRUD**  
   Django ORM permite crear, leer, actualizar y eliminar registros de cada modelo de manera sencilla, sin necesidad de preocuparse por integridad referencial entre tablas.

## Ejemplo de modelo independiente

Para ilustrar esta implementación, se puede crear un modelo `Producto` con campos básicos:

```python
from django.db import models

class Producto(models.Model):
    nombre = models.CharField(max_length=100)
    precio = models.DecimalField(max_digits=10, decimal_places=2)
    cantidad = models.PositiveIntegerField()

    def __str__(self):
        return self.nombre
```

- nombre: almacena el nombre del producto.
- precio: registra el valor del producto con precisión decimal.
- cantidad: indica el stock disponible, solo permitiendo valores positivos.

Este modelo genera automáticamente una tabla producto en la base de datos, completamente independiente de otras entidades.

## Ventajas de usar modelos no relacionados

- Simplificar la estructura de la base de datos para aplicaciones pequeñas o prototipos.
- Facilitar la administración de datos sin necesidad de definir llaves foráneas.
- Permitir un desarrollo rápido de funcionalidades básicas sin complicaciones de integridad referencial.