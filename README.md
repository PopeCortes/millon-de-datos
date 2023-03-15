
# Registros de millon de datos



## Código en PHP

```php
<?php

$servername = "localhost"; 
$username = "root";
$password = "";
$dbname = "millon";
$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Error de conexión: " . $conn->connect_error);
}

for ($i = 1; $i <= 1000000; $i++) {

    $nombres = ['Juan', 'María', 'Pedro', 'Ana', 'Luis', 'Carla', 'Pablo', 'Lucía', 'Huervo', 'Diego', 'Barron', 'Alexia', 'Fernando', 'Zahira'];
    $apellidos = ['Pérez', 'Gómez', 'García', 'López', 'Hernández', 'Rodríguez', 'Valdez', 'Espinoza', 'Esquivel', 'Mora', 'Fernandez', 'Amador'];

    $conteo = count($nombres);
    $nombreAleatorio = mt_rand(0, $conteo - 1);
    $incertnom = $nombres[$nombreAleatorio];
    // Generar datos aleatorios
    $nombre = $incertnom . $i;
    $apellido = $incertnom . $i;

    // Insertar el registro en la tabla
    $sql = "INSERT INTO millon (nombre, apellido)
          VALUES ('$nombre', '$apellido')";

    if ($conn->query($sql) === TRUE) {
        echo "Registro insertado correctamente: " . $i . "<br>";
    } else {
        echo "Error al insertar registro: " . $conn->error;
    }

    sleep(0.1);
}

$conn->close();

?>
```

Para que te imprima el millon de datos, tienes que irte a xampp, despues te vas a ir a la confifuracion de apache y en la configuracion de apache le das clic al que dice "PHP", despues vas a buscar "max_execution_time=120" al ver de que sea 120, le vamos a dejas solamente el "0" y los guardamos, despues cerramos xampp y lo volvemos a iniciar y ejecutamos el codigo en el navegador.
