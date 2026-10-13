# Checklist de Viaje — app para Android

App que arma el checklist del viaje según las fechas, el destino y cómo viajan.
Funciona sin internet y guarda las tildes en el teléfono.

## Opción A: compilar con Android Studio (en tu computadora)

1. Instalá Android Studio (gratis): https://developer.android.com/studio
2. Descomprimí este .zip y en Android Studio elegí **File > Open** y abrí la carpeta `ChecklistViaje`.
3. Esperá a que termine la sincronización (la primera vez descarga varias cosas y puede tardar unos minutos).
4. Para probarla en tu teléfono:
   - En el teléfono activá las **Opciones de desarrollador** (Ajustes > Acerca del teléfono > tocar 7 veces "Número de compilación") y dentro de ellas la **Depuración USB**.
   - Conectá el teléfono por USB y tocá el botón verde ▶ (Run).
5. Para generar el archivo instalable: **Build > Build App Bundle(s) / APK(s) > Build APK(s)**.
   El archivo queda en `app/build/outputs/apk/debug/app-debug.apk`. Pasalo al teléfono (WhatsApp, Drive, cable) y abrilo para instalar.
   Android te va a pedir permiso para "instalar apps de origen desconocido": es normal porque no viene de Play Store.

## Opción B: que GitHub compile el APK (sin instalar nada)

1. Creá un repositorio en https://github.com y subí el contenido de la carpeta `ChecklistViaje`
   (incluida la carpeta oculta `.github`).
2. Entrá a la pestaña **Actions**: se ejecuta solo "Generar APK" (tarda unos 5 minutos).
3. Al terminar, el APK queda publicado en la sección **Releases** del repositorio (también en Actions, dentro de un .zip).
   Enlace directo a la última versión: https://github.com/Sergiorio4/cheklist-viaje/releases/latest/download/ChecklistViaje.apk
4. Pasá el APK al teléfono e instalalo.

## Cómo modificar el contenido

Toda la lista está en `app/src/main/assets/www/index.html`, en la parte `SECTIONS`.
Cada ítem es una línea del tipo:

    I('Texto del ítem', 'nota opcional', 'momento', condición)

- momento: `sem` (una semana antes), `dias` (1 a 2 días antes), `sal` (día de salida), `via` (durante el viaje).
- condición: `A` (solo si viajan en auto), `K` (con chicos), `P` (con mascota), `C` (camping), `X` (exterior).

Ese mismo archivo se puede abrir en el navegador de la computadora para probar los cambios antes de compilar.

## Datos técnicos

- Android 8.0 o superior (minSdk 26), targetSdk 34.
- WebView con los archivos locales (androidx.webkit WebViewAssetLoader); sin permisos especiales.
- "Compartir pendientes" abre el menú de compartir de Android (WhatsApp, Gmail, notas, etc.).
- El APK de depuración sirve para uso personal. Para publicar en Play Store hace falta firmarlo y subir targetSdk a 35.
