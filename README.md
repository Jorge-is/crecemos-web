# Crecemos Web

Página de descarga de la app móvil **Crecemos**. Es HTML estático, sin build: se publica con GitHub Pages.

- Web: https://jorge-is.github.io/crecemos-web/
- APK: https://github.com/Jorge-is/crecemos-web/releases/latest/download/crecemos.apk
- QR de la web: `qr-crecemos.png` (para proyectar o imprimir) y `qr-crecemos.svg`.

iPhone figura como "próximamente": iOS no instala un archivo desde una página web, necesita TestFlight o App Store.

## Actualizar el APK

El enlace usa `releases/latest`, así que la web y el QR no cambian. Se compila la app, se renombra el archivo a `crecemos.apk` y se publica una nueva versión:

```sh
cd ../crecemos-app/android && ./gradlew assembleRelease
gh release create v1.1 app/build/outputs/apk/release/app-release.apk#crecemos.apk --title "Crecemos 1.1"
```

## Regenerar el QR

```sh
npx qrcode -e H -w 1024 -m 2 -d 1A1016 -l FFFFFF -o qr-crecemos.png "https://jorge-is.github.io/crecemos-web/"
```

El APK está firmado con la clave de depuración de la plantilla: sirve para instalarlo a mano, no para una tienda.
