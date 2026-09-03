# From Video to Frames 🎬 ➡️ 🖼️

Herramienta web ligera para convertir vídeos en secuencias de fotogramas JPG optimizados para web (animaciones por scroll, interactividad estilo Apple, canvas o galerías).

Funciona **100% en local en el navegador**: ningún vídeo sale de tu ordenador. No requiere servidores, bases de datos ni Node.js.

---

## 🚀 Inicio Rápido

1. Clona el repositorio:
   ```bash
   git clone git@github.com:MiguelFreire18/from-video-to-Frames.git
   cd from-video-to-Frames
   ```
2. Abre `index.html` en cualquier navegador (Chrome, Safari, Firefox, Edge):
   - **macOS:** `open index.html`
   - **Linux:** `xdg-open index.html`
   - **Windows:** `start index.html`
3. Arrastra tu vídeo, ajusta los fotogramas y la calidad, y pulsa **"Comenzar Exportación"**. Al finalizar, descarga el paquete completo en `.ZIP`.

---

## 💡 Consejos de Exportación para Web

Para animaciones de scroll fluido (scrollytelling) sobre `<canvas>`:

| Duración Vídeo | Frames Recomendados | FPS Efectivo | Calidad JPG | Uso Recomendado | Peso Estimado Total |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **5 segundos** | 60 - 75 frames | 12 - 15 fps | 80% | Scroll fluido estándar | ~3 - 5 MB |
| **10 segundos** | **120 - 150 frames** | **12 - 15 fps** | **80%** | **Equilibrio óptimo (Recomendado)** | **~6 - 9 MB** |
| **10 segundos** | 240 frames | 24 fps | 75% | Máxima fluidez cinematográfica | ~14 - 18 MB |
| **15 segundos** | 180 - 225 frames | 12 - 15 fps | 75% | Scroll largo de producto | ~10 - 14 MB |

### Claves para el rendimiento en web:
1. **No uses 60 fps:** Para animaciones controladas por scroll, el ojo humano no distingue entre 15 y 60 fps, pero tu web pesará 4 veces más.
2. **Escala la resolución:** A menos que sea pantalla completa 4K, exportar a **1080p (1920px)** o **720p (1280px)** reduce el tamaño a la mitad sin pérdida visual apreciable en pantallas Retina.
3. **Calidad 80%:** El algoritmo JPEG a 80% elimina artefactos visibles manteniendo los archivos por debajo de 50-70 KB por fotograma.

---

## 🛠️ Instalación Automática de Dependencias (FFmpeg CLI)

La interfaz incluye un generador de comandos `ffmpeg` por si prefieres procesar vídeos grandes por terminal. Si no tienes `ffmpeg` instalado, usa el comando correspondiente a tu sistema:

### macOS
Con Homebrew:
```bash
brew install ffmpeg
```
Instalación binario estático directo (sin Homebrew):
```bash
curl -L https://github.com/eugeneware/ffmpeg-static/releases/download/b6.1.1/ffmpeg-darwin-arm64.gz | gzip -d > /usr/local/bin/ffmpeg && chmod +x /usr/local/bin/ffmpeg
```

### Linux (Debian / Ubuntu)
```bash
sudo apt update && sudo apt install -y ffmpeg
```

### Windows
Con Winget:
```powershell
winget install Gyan.FFmpeg
```
Con Chocolatey:
```powershell
choco install ffmpeg
```

---

## ⌨️ Comando FFmpeg Rápido

Para extraer fotogramas manualmente desde la consola:

```bash
# Extraer 12 fotogramas por segundo a calidad alta JPG:
ffmpeg -i video.mp4 -vf "fps=12,scale=1920:-1" -qscale:v 2 frame_%04d.jpg
```

---

## 🔒 Privacidad y Seguridad

- **100% Client-Side:** Todo el renderizado y compresión ocurre dentro del motor de tu navegador mediante HTML5 Canvas y JSZip.
- **Sin telemetría ni cookies.**
- **No se recopila ningún dato personal.**
