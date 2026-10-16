# SENSAKART

Juego de karts 3D (Three.js) de **Sensastreaming**. Es una web (PWA con modo offline) y una app iOS (Capacitor).

## Estructura
```
sensakart/
├── www/                      ← TODO el juego (es lo que se publica y lo que va dentro de la app iOS)
│   ├── index.html · manifest.json · service-worker.js
│   ├── css/style.css
│   ├── js/ main · kart · track · controls · hud · sky · scenery · effects · audio
│   ├── kart.glb · cangri.glb
│   ├── icons/ · vendor/three/ (Three.js incluido, sin CDN)
├── resources/icon-1024.png   ← icono de la app iOS
├── sensastreaming-integration/   ← sección y página para la web de Sensastreaming
├── capacitor.config.json · package.json · configure-ios.sh
└── .github/workflows/pages.yml   ← publica www/ en GitHub Pages
```

## Publicar en GitHub Pages
1. Crea el repositorio nuevo `sensakart` en GitHub y sube TODO el contenido de esta carpeta (incluida `.github`).
2. En el repositorio: Settings → Pages → Build and deployment → Source: **GitHub Actions**.
3. En 1–2 minutos queda en `https://TU-USUARIO.github.io/sensakart/`.

## Probar en tu computador
`python3 -m http.server 8000 --directory www` y abre http://localhost:8000

## App iOS (Mac con Xcode 26+ y Node 22+)
```
npm install
npx cap add ios
./configure-ios.sh
npx cap sync ios
npx cap open ios
```
En Xcode: Signing & Capabilities → tu Team → elige simulador o iPhone → ▶.
Cada vez que cambies algo en `www/`: `npx cap sync ios`.

## Al cambiar archivos del juego
Sube el número `VERSION` en `www/service-worker.js` (`sensakart-v2`, `v3`…) para que los móviles descarguen la versión nueva.
