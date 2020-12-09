# ExamenPhp

### Autor: Alberto J. Mañas González
## Primera pregunta:
En el codigo del CRUD orientado a objetos, modifica lo necesario para que figure el símbolo del dola a la izuiqrda del precio, en el listado de los productos y en el detalle (read_one). Explica los cambios realizados. Realiza un commit.

En index.php:
```php
$dolar = "$";
echo "<tr>";
    echo "<td>{$id}</td>";
    echo "<td>{$name}</td>";
    echo "<td>{$description}</td>";
    echo "<td>{$dolar}{$price}</td>";
    echo "<td>";
```
Añadir en price una variable con el simbolo dolar.


En read_one añadir símbolo dolar antes de la sentencia php:
```html
   <tr>
        <td>Price</td>
        <td>$<?php echo htmlspecialchars($price,?></td>
    </tr>
```

## Segunda pregunta:
Explica como se guarda la imagen de un producto en la base de datos: tipo de formado del campo, comprobaciónes realizadas antes de aceptar una imagen, que se guarda en la B.D. dónde está la imágen, como recuperarla..etc.

La imagen de un producto de guarda a través de la superglobal $_FILES. a través de variables reservadas de la misma subglobal podemos acceder a su:

Para ello también es necesario modificar el formulario para que:

```php
<form action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>" method="post" enctype="multipart/form-data">
```

```php


$file_type // Tipo de la imagen, por ejemplo "JPG", "JPEG", "PNG" ..etc.

$tmp_name // El nombre de dicha imagen para hacer referencia a ella.
```