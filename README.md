# ESTRUENDO STEM MIXER

Aplicación Android nativa para biblioteca musical, reproducción, futura separación de stems con IA y mezcla multipista.

## Estado del proyecto

- Etapa 1: base Android, interfaz inicial y escaneo de biblioteca local.
- Etapa 2: integración inicial de Media3 ExoPlayer, controles de reproducción y MediaSessionService para notificación/controles multimedia en segundo plano y pantalla bloqueada.
- Pendiente: pruebas reales en dispositivo, decodificación ampliada con FFmpeg, motor DSP, separación IA y guardado de sesiones.

## Formatos de audio

La biblioteca del dispositivo muestra los archivos de audio indexados por Android. El botón Importar usa el selector de documentos para elegir audio fuera de la biblioteca indexada. En esta etapa, la reproducción depende de los decodificadores disponibles en Android y Media3; no se promete compatibilidad universal. La etapa de decodificación ampliada evaluará FFmpeg y sus licencias para añadir formatos/códecs adicionales.

## Requisitos de compilación

- JDK 17
- Gradle 8.9
- Android SDK Platform 35 y Build Tools 35.0.0
- Android Gradle Plugin 8.7.3

## Compilar desde GitHub Actions sin instalar herramientas en el teléfono

1. Crear un repositorio GitHub nuevo.
2. Subir el contenido de esta carpeta a la raíz del repositorio.
3. Abrir la pestaña Actions y permitir los workflows si GitHub lo solicita.
4. Ejecutar `Build Android APK` con `Run workflow`.
5. Al terminar, abrir la ejecución y descargar el artefacto `ESTRUENDO-STEM-MIXER-debug`.
6. Descomprimirlo en el teléfono e instalar `app-debug.apk`. Android puede pedir autorización para instalar aplicaciones desde el navegador/gestor de archivos.

El workflow incluido instala Java, Gradle y Android SDK en un runner de GitHub y compila el APK debug.

## Estructura

- `app/src/main/java/.../data`: biblioteca local.
- `app/src/main/java/.../playback`: servicio de reproducción.
- `app/src/main/java/.../MainActivity.kt`: interfaz y controles básicos.
- `.github/workflows/android-apk.yml`: compilación remota del APK.

## Limitaciones actuales

No incluye todavía separación IA, canales de mezcla multipista, efectos DSP ni guardado de proyectos. La reproducción de fondo y pantalla bloqueada está implementada en código pero debe validarse en un dispositivo Android real; las políticas de batería del fabricante pueden afectar el comportamiento.
