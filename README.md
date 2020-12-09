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

Para ello también es necesario modificar el formulario para que se permitan ficheros y poder así cargar una imagen. 

Para subir la imagen a una base de datos es necesario comprobar si dicha imagen ya está guardada en ella, que cumple las extensiones requeridas programadas como filtro antes de la DB.
Para ello se debe realizar las comprobaciones de a continuación:

 - Comprobar si el usuario ha seleccionado un archivo de imagen para subirlo.
 - Recuperar el contenido del archivo de la imagen mediante el tmp_name.
 - Crear la conexión a la base de datos y seleccionarla.
 - Insertar el contenido binario de la imagen en la tabla (Solo si no quieres almacenarlo en el servidor por temas de espacio).
 - Mostrar el estado de la subida de la imagen al usuario.

 Por otra parte, para recuperar la imagen es necesario basarse en el Id. Después, se mostrará la imagen en la página web. Para renderizar el archivo de imagen en la página web será necesario utulizar un header Content-type.
 ```php
  //Obtener imagen de la DB
    $result = $db->query("SELECT image FROM images WHERE id = {$_GET['id']}");
    
    if($result->num_rows > 0){
        $imgData = $result->fetch_assoc();
        
        //Renderizar imagen con Content-type.
        header("Content-type: image/jpg"); 
        echo $imgData['image']; 
    }else{
        echo 'Image not found...';
    }
 ```

```php
<form action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>" method="post" enctype="multipart/form-data">
```

Añadir un campo

```php
$file_type // Tipo de la imagen, por ejemplo "JPG", "JPEG", "PNG" ..etc.

$tmp_name // El nombre de dicha imagen para hacer referencia a ella.
```


## Ejercicio 6:
Para actualizar la imagen hay que modificar ```update.php``` hay que añadir la imagen para poder realizar el select de la query.

Además, hay que crear el row para updatear la query y así realizar el método post de la imagen.
Por otro lado, es necesario añadir el parametro de la imagen para añadir el tr que contendrá la imagen.