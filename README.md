<div align="center">

# ScanFest (Sistema de Gestión de Eventos con Registro de Usuarios y Códigos QR)
</div>

### Descripción:
Este proyecto consiste en desarrollar un sistema web para gestionar eventos y usuarios. La plataforma permite a los usuarios registrarse en eventos, generar códigos QR para cada evento, y gestionar la información de los usuarios y eventos a través de una interfaz web intuitiva. Los usuarios pueden crear una cuenta, iniciar sesión y gestionar su perfil, mientras que los administradores pueden crear y administrar eventos, y supervisar el registro de usuarios.

## Roles
`Administrador:`
- Usuarios: Ver Usuarios, Crear Usuarios, Editar Usuarios, Eliminar Usuarios, Buscar Usuario por datos
- Eventos: Ver Eventos, Crear Eventos, Editar Eventos, Eliminar Eventos, Buscar Evento por datos
- Registros: Ver Registros, Crear Registros, Editar Registros, Eliminar Registros, Buscar Registro por datos
- QR: Ver QR, Crear QR, Editar QR, Eliminar QR, Buscar QR por datos

`Trabajador:`
- Usuarios: Ver Usuarios, Crear Usuarios, Editar Usuarios, Buscar Usuario por datos
- Eventos: Ver Eventos, Crear Eventos, Editar Eventos, Buscar Evento por datos
- Registros: Ver Registros, Crear Registros, Editar Registros, Buscar Registro por datos
- QR: Ver QR, Crear QR, Editar QR, Buscar QR por datos

` Cliente:`
- Eventos: Ver Eventos, Buscar Evento por datos
- QR: Ver QR, Buscar QR por datos

## Vistas
Inicio: index
Perfil: profile
Iniciar Sesion: login
Crear Cuenta: registration
Mantenimiento: maintenance
### Errores
404 Not Found
408 Request Timeout
503 Service Unavailable

## Tecnologías Utilizadas:
- HTML: Estructura del contenido web.
- CSS: Diseño y formato de la interfaz de usuario.
- JavaScript (JS): Lógica del lado del cliente e interactividad.
- Bootstrap: Framework CSS para crear una interfaz de usuario responsiva.
- Bootstrap Icons: Biblioteca de íconos moderna.
- MySQL: Base de datos para gestionar información de usuarios, eventos y códigos QR.
- Node.js: Entorno de ejecución para desarrollo de backend.
- Express.js: Framework para Node.js para simplificar rutas y servidor.
- Sequelize: ORM para interactuar con MySQL desde Node.js.

## Funcionalidades Clave:
### Gestión de Usuarios:
- Registro e inicio de sesión de usuarios.
- El administrador puede ver la lista de usuarios, registrados, eventos y QR, y buscar por nombre.
- Gestión de perfiles, incluyendo imagen de perfil y datos de contacto.
- Recuperación de contraseñas y verificación de correos.
. Gestión del estado de la cuenta (activa/inactiva).
### Gestión de Eventos:
- Creación y edición de eventos con nombre, descripción, lugar, fecha y hora.
- Eliminación lógica de eventos (sin borrar registros físicamente).
### Registro en Eventos:
- Los usuarios pueden registrarse en eventos.
- Registro de la fecha de inscripción.
- Generación de Códigos QR:
- Generación de códigos QR para acceso o validación en eventos.
- Control de validez con fechas de expiración.

## Tablas:
- Usuarios:
Id
Nombre
Apellido
Teléfono
Estado (Activo/Inactivo)
Correo Electrónico
Contraseña
Cambio de Contraseña
Código de Recuperación
Expiración del Código
Imagen perfil
Fecha de Creación
Fecha de Eliminación
Última Sesión
Token de Verificación
- Eventos:
Id
Nombre
Descripción
Lugar
Fecha
Hora
Fecha de Creación
Fecha de Eliminación
- Registros:
Id
Id del Usuario
Id del Evento
Fecha de Registro
- Código QR:
Id
Id del Evento
Código QR
Fecha de Generación
Fecha de Expiración

## Estructura del Sistema
- Estructura
  ```bash
  /ScanFest
  ├── /css
  │     ├── body.css
  │     ├── dark_mode.css   
  │     ├── light_mode.css  
  │     ├── profile.css  
  │     ├── login.css 
  │     └── register.css        
  ├── /excel
  │     ├── Events.xlsx
  │     ├── Registered.xlsx
  │     └── QR.xlsx
  ├── /js
  │     ├── db.connection.js
  │     ├── authentication.js
  │     ├── redirection.js
  │     ├── qr_generation.js
  │     ├── event_management.js
  │     └── user_management.js
  ├── /views
  │     ├── profile.html
  │     ├── login.html
  │     ├── register.html
  │     ├── dashboard.html
  │     └── event_registration.html
  ├── /img
  │     └── perfil_predeterminado.png
  ├── /qr_codes
  │     └── event_qr_<event_id>.png
  ├── index.html 
  ├── server.js   
  ├── /db
  │     └── db.config.js
  ├── /models 
  │     ├── user.model.js
  │     ├── event.model.js
  │     ├── registration.model.js
  │     └── qr.model.js
  ├── /routes
  │     ├── user.routes.js 
  │     ├── event.routes.js
  │     ├── qr.routes.js 
  │     └── registration.routes.js 
  └── /controllers
        ├── user.controller.js 
        ├── event.controller.js 
        ├── qr.controller.js  
        └── registration.controller.js

## Explicación de la Estructura:
/css: Estilos CSS para vistas y temas (modo oscuro y claro).
/excel: Archivos Excel generados (eventos, registrados, QR).
/js: Lógica del cliente: autenticación, redirección, generación de QR, gestión de eventos y usuarios.
/views: Páginas HTML (perfil, login, registro, etc.).
/img: Imágenes como el perfil predeterminado.
/qr_codes: Códigos QR generados para cada evento.
index.html: Página principal.
server.js: Configuración de Express.js y servidor.
/db: Configuración de la base de datos.
/models: Modelos de las tablas (definidos con Sequelize).
/routes: Endpoints de la API (usuarios, eventos, QR, registros).
/controllers: Lógica de negocio para cada funcionalidad.

## Configuración para IP específica:
En el archivo server.js, configura el host y puerto para restringir el acceso solo a una IP específica:
const host = '192.168.1.100';
const port = 5000;
app.listen(port, host, () => {
    console.log(`Server running at http://${host}:${port}/`);
});
