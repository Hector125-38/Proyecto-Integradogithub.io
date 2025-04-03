# Proyecto de Control de Acceso RFID

Este proyecto utiliza un ESP32 y un módulo RFID RC522 para leer tarjetas RFID y enviar los datos a una base de datos. Además, se incluye una página web para mostrar los accesos y gestionar los registros.

## Contenido del Proyecto

1. **Código para ESP32**: Implementación del código que permite leer tarjetas RFID.
2. **Página Web**: Interfaz para mostrar los registros de acceso.
3. **Base de Datos**: Almacenamiento de los datos leídos de las tarjetas.

## Estructura del Proyecto

```
/proyecto-rfid
│
├── esp32_code.ino          # Código para el ESP32
├── index.html              # Página web principal
├── styles.css              # Estilos CSS para la página web
└── script.js               # Script JavaScript para manejar la lógica de la página
```

## Descripción de la Página Web

La página web se encarga de mostrar los registros de acceso de las tarjetas RFID. A continuación se presenta el código HTML básico:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Control de Acceso RFID</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Registro de Tarjetas RFID</h1>
    <table>
        <thead>
            <tr>
                <th>ID</th>
                <th>UID</th>
                <th>Nombre</th>
                <th>Acceso</th>
                <th>Fecha de Registro</th>
            </tr>
        </thead>
        <tbody id="tabla-body">
            <!-- Aquí se insertarán los datos dinámicamente -->
        </tbody>
    </table>
    <script src="script.js"></script>
</body>
</html>
```

### Funcionalidades

- **Obtiene los datos de la API en PHP**: La página web se conecta a una API que devuelve los registros de acceso.
- **Llena la tabla de la página web con los registros de las tarjetas**: Los datos se muestran dinámicamente en la tabla.

### Código JavaScript

El siguiente código JavaScript se encarga de obtener los datos y llenar la tabla:

```javascript
fetch('url_de_tu_api')
    .then(response => response.json())
    .then(data => {
        let tbody = document.getElementById("tabla-body");
        tbody.innerHTML = "";
        data.forEach(registro => {
            let fila = `<tr>
                <td>${registro.id}</td>
                <td>${registro.uid}</td>
                <td>${registro.nombre}</td>
                <td>${registro.acceso ? '✅' : '❌'}</td>
                <td>${registro.fecha_registro}</td>
            </tr>`;
            tbody.innerHTML += fila;
        });
    })
    .catch(error => console.error("Error al obtener datos:", error));
```

## Próximos Pasos

1. **Agregar CSS para mejorar el diseño**: Se puede personalizar el estilo de la página web para que sea más atractiva.
2. **Desplegar todo en un servidor local o en la nube**: Configurar un entorno de servidor para que la aplicación sea accesible desde cualquier lugar.

## Contribuciones

Las contribuciones son bienvenidas. Si deseas colaborar, por favor abre un issue o envía un pull request.

## Licencia

Este proyecto está bajo la Licencia MIT. Para más detalles, consulta el archivo LICENSE.
```

Este `README.md` proporciona una visión general clara del proyecto, su estructura y los pasos a seguir. Puedes personalizarlo según tus necesidades y agregar más detalles si es necesario.
