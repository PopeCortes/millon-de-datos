
# Registros de millon de datos



## Usage/Examples

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
