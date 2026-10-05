# Cuentas de factoring: instalar como app y respaldo en OneDrive

Archivos de esta carpeta: `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`.
Los 5 se suben juntos, en la misma carpeta, sin cambiarles el nombre.

## Parte 1. Publicar en GitHub Pages (gratis)

1. Entra a https://github.com y crea una cuenta (o inicia sesión).
2. Arriba a la derecha toca **+** y luego **New repository**.
3. Nombre del repositorio: `factoring`. Déjalo en **Public** y toca **Create repository**.
   Solo el código de la app queda público. Tus cuentas y montos no se suben a GitHub.
4. En la página del repositorio toca **uploading an existing file**.
5. Arrastra (o elige) los 5 archivos y toca **Commit changes**.
6. Ve a **Settings** y luego **Pages**.
7. En **Source** elige **Deploy from a branch**. En **Branch** elige `main` y la carpeta `/ (root)`. Toca **Save**.
8. Espera 1 o 2 minutos y recarga. Arriba aparece tu dirección:
   `https://TU-USUARIO.github.io/factoring/`
   Anótala con la barra final `/`. La necesitas en la Parte 3.

## Parte 2. Instalarla como app en Android (Chrome)

1. Abre tu dirección `https://TU-USUARIO.github.io/factoring/` en Chrome.
2. Toca el botón **Instalar como app** de la página, o el menú ⋮ de Chrome y luego **Instalar app**.
3. Confirma. Queda un icono "Factoring" en tu pantalla de inicio y abre sin barra del navegador.
4. Para pasar tus cuentas actuales: en la versión vieja toca **Respaldo (.json)**, y en la app nueva **Cargar respaldo** y elige ese archivo.

Los datos de la app nueva son independientes de la versión anterior, por eso hay que pasarlos con el respaldo.

## Parte 3. Respaldo automático en OneDrive

La app guarda en OneDrive, en la carpeta **Apps**, dentro de una carpeta propia: un archivo `factoring-respaldo.json` siempre actualizado y una copia por día `factoring-AAAA-MM-DD.json`.
Para que Microsoft permita esa conexión hay que registrar la app una sola vez (gratis).

### 3.1 Registrar la app en Microsoft
1. Entra a https://entra.microsoft.com con tu cuenta de Microsoft.
   Si te pide crear un directorio o una cuenta de Azure gratuita, acepta. Puede pedir una tarjeta solo para verificar y no cobra por esto.
2. Ve a **Identidad** (Identity), luego **Aplicaciones**, **Registros de aplicaciones** (App registrations), y toca **Nuevo registro** (New registration).
3. Nombre: `Factoring`.
4. Tipos de cuenta compatibles: **Cuentas en cualquier directorio organizativo y cuentas personales de Microsoft**.
5. URI de redirección: en la lista elige **Aplicación de página única (SPA)** y escribe tu dirección completa, por ejemplo `https://TU-USUARIO.github.io/factoring/` (con la `/` al final, igual a como aparece en la app).
6. Toca **Registrar**.
7. En la pantalla que aparece copia el **Id. de aplicación (cliente)**, que son 36 caracteres con guiones.
8. En **Permisos de API** toca **Agregar un permiso**, **Microsoft Graph**, **Permisos delegados**, y marca `Files.ReadWrite.AppFolder` y `offline_access`. Guarda. No hace falta consentimiento de administrador.

Los nombres de los menús de Microsoft cambian de vez en cuando, pero los pasos son esos.

### 3.2 Conectar desde la app
1. Abre la app y toca **OneDrive**.
2. Pega el Id. de aplicación (cliente) y toca **Conectar**.
3. Inicia sesión en Microsoft y acepta el permiso.
4. Al volver, la línea de arriba dice "OneDrive: respaldo guardado". Desde ahí cada cambio se respalda solo.

## Cosas que debes saber

- La sesión con Microsoft para páginas web dura unas 24 horas. Si pasó más tiempo, la línea de arriba te avisa en rojo. Toca **OneDrive** y **Conectar** y entra con un toque.
- Si cambias la dirección de la app, hay que cambiar también el URI de redirección en Microsoft.
- Con **Compartir respaldo** puedes mandar el archivo a Google Drive, WhatsApp, correo, etc.
- Si cambias archivos en GitHub y la app no se actualiza, cierra y vuelve a abrirla una o dos veces.
