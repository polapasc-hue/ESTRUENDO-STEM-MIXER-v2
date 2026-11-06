# Cómo continuar desde un teléfono Android sin una app de programación

La opción más sencilla es compilar el proyecto en GitHub Actions desde el navegador. El teléfono solo necesita navegador, conexión a Internet y una cuenta GitHub.

## A. Preparar el proyecto

1. Descarga `ESTRUENDO_STEM_MIXER_ETAPA2.zip` en tu teléfono.
2. Descomprímelo con el administrador de archivos del teléfono. Debe quedar una carpeta `ESTRUENDO_STEM_MIXER`.
3. Dentro de esa carpeta deben verse `app`, `build.gradle.kts`, `settings.gradle.kts` y `README.md`.

## B. Crear el repositorio

1. Abre `https://github.com` en Chrome e inicia sesión o crea una cuenta.
2. Pulsa **New repository**.
3. Nombre: `estruendo-stem-mixer`.
4. Selecciona **Private** (recomendado) y crea el repositorio vacío. No agregues README ni licencia porque el proyecto ya tiene esos archivos.

## C. Subir los archivos

1. En el repositorio, usa **Add file → Upload files**.
2. Sube el contenido de la carpeta `ESTRUENDO_STEM_MIXER`, conservando las carpetas. Es importante que `.github/workflows/android-apk.yml` quede en esa ruta exacta dentro del repositorio.
3. Si el navegador móvil no te deja subir la carpeta oculta `.github`, súbelo todo lo demás y luego usa **Add file → Create new file**: escribe `.github/workflows/android-apk.yml` como nombre del archivo (las barras crean las carpetas) y pega el contenido del `android-apk.yml` incluido en el ZIP. No subas solo el ZIP.
4. Confirma con **Commit changes**.

## D. Compilar el APK en GitHub

1. Abre la pestaña **Actions** del repositorio.
2. Si aparece una solicitud para habilitar workflows, acéptala.
3. Selecciona **Build Android APK**.
4. Pulsa **Run workflow** y luego confirma.
5. Espera a que la ejecución termine en verde.
6. Abre la ejecución y descarga el artefacto `ESTRUENDO-STEM-MIXER-debug`.
7. Descomprime el artefacto y toca `app-debug.apk` para instalarlo. Autoriza temporalmente la instalación desde la aplicación que utilizaste para abrirlo si Android lo solicita.

## E. Probar la etapa 2

- Abre ESTRUENDO STEM MIXER.
- Concede permiso para leer audio.
- Pulsa **ESCANEAR** y selecciona una canción.
- Toca una canción de la lista para reproducirla.
- Bloquea la pantalla: Android debería mostrar los controles multimedia de la sesión.
- Prueba **IMPORTAR** para seleccionar un archivo desde otra carpeta.

## Límites conocidos

- Esta versión todavía no es una separación de stems ni un mezclador multipista.
- La compatibilidad de códecs depende de Android/Media3; la compatibilidad ampliada con FFmpeg se implementará y validará después.
- La reproducción en pantalla bloqueada está preparada con MediaSessionService, pero debe probarse en el teléfono. Algunos fabricantes aplican restricciones de batería.
- El workflow compila un APK de depuración, no una versión firmada para publicar en Play Store.
