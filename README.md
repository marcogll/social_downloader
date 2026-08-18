<p align="center">
  <a href="https://soul23.mx">
    <picture>
      <source
        media="(prefers-color-scheme: dark)"
        srcset="https://raw.githubusercontent.com/marcogll/mg_data_storage/refs/heads/main/soul23/logo/soul23_logo_wh.png">
      <source
        media="(prefers-color-scheme: light)"
        srcset="https://raw.githubusercontent.com/marcogll/mg_data_storage/refs/heads/main/soul23/logo/soul23_logo_blk.png">
      <img
        src="https://raw.githubusercontent.com/marcogll/mg_data_storage/refs/heads/main/soul23/logo/soul23_logo_blk.png"
        width="110"
        alt="Soul:23">
    </picture>
  </a>
</p>

<h1 align="center">TikTok Telegram</h1>

<p align="center">
  Descarga videos de redes sociales (FB, IG, X, TikTok) con un bot de Telegram.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3a3a3a?style=flat-square&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/Telegram-3a3a3a?style=flat-square&logo=telegram&logoColor=white">
  <img src="https://img.shields.io/badge/yt-dlp-3a3a3a?style=flat-square&logo=youtube&logoColor=white">
</p>

---

## Description

Bot de Telegram para descargar videos de redes sociales (Facebook, Instagram, X, TikTok): envía el enlace del video y recibe el archivo descargado, con configuración por variables de entorno.

Python con python-telegram-bot y yt-dlp.

## ✨ Características Principales

* 🎯 **Multi-Plataforma**: Soporta TikTok (sin marca de agua), Instagram (reels, posts, stories), Facebook y X (Twitter).
* 🔒 **Control de Acceso Estricto**: Solo procesa enlaces enviados por usuarios autorizados (mediante su ID de Telegram).
* 🧹 **Auto-Limpieza de Disco**: Recolector en segundo plano que elimina los videos locales tras X horas.
* 🔄 **Auto-Actualización Inteligente**: Actualiza `yt-dlp` cada 24h y reinicia automáticamente si hay nueva versión.
* ⚙️ **Inicio con Sistema**: Script de arranque y servicio systemd incluidos.

---

## 🛠️ Requisitos Previos

* Python 3.9 o superior
* FFmpeg instalado en el sistema

Instalación de FFmpeg según sistema:

* **Arch Linux**: `sudo pacman -S ffmpeg`
* **Ubuntu / Debian**: `sudo apt install ffmpeg`
* **macOS**: `brew install ffmpeg`

---

## 📦 Instalación

1. Clona o descarga los archivos.

2. Crea un entorno virtual:
   ```bash
   python -m venv .venv
   ```

3. Activa el entorno virtual:
   ```bash
   source .venv/bin/activate
   ```

4. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

---

## ⚙️ Configuración

### Obtener credenciales de Telegram

Para usar el bot necesitas crear una aplicación en Telegram:

1. Ve a [my.telegram.org](https://my.telegram.org) e inicia sesión con tu número de teléfono.
2. Click en **"API Development Tools"**.
3. Completa los datos:
   - **App title**: Nombre de tu aplicación (ej: TikTok Downloader Bot)
   - **Short name**: Nombre corto (ej: tiktokdl)
   - **URL**: Tu repositorio o sitio web (puede ser vacío)
   - **Platform**: Mobile
   - **Description**: Descripción breve (puedes poner "Bot para descargar videos")
4. Click en **"Create application"**.
5. Copia los valores:
   - **api_id**: Es un número (ej: `1234567`)
   - **api_hash**: Es una cadena larga de letras y números (ej: `a1b2c3d4e5f6...`)

**⚠️ IMPORTANTE**: Nunca compartas tu `API_HASH`. Es equivalente a una contraseña.

### Configurar variables de entorno

Copia `.env.example` a `.env` y configura:

```env
# Credenciales de Telegram
API_ID=tu_api_id
API_HASH=tu_api_hash
PHONE=+521234567890

# Usuarios permitidos (IDs separados por comas)
USUARIOS_AUTORIZADOS=123456789,987654321

# Configuración
LOG_LEVEL=INFO
CLEANUP_HOURS=168

# Grupo donde escuchará enlaces
GRUPO_DESTINO=-1009876543210
CARPETA_DESCARGAS_SOCIAL=./social_downloads
```

---

## 🚀 Uso

### Manual:
```bash
./start_bot.sh
```

### Con systemd (inicio automático):
```bash
sudo cp social-downloader.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable social-downloader
sudo systemctl start social-downloader
```

---

## 📝 Comandos útiles

* `sudo systemctl status social-downloader` - Ver estado
* `sudo systemctl restart social-downloader` - Reiniciar
* `tail -f bot.log` - Ver logs en tiempo real

---

## 📋 Enlaces soportados

* **TikTok**: `tiktok.com/@usuario/video/xxx`, `vm.tiktok.com/xxx`, `vt.tiktok.com/xxx`
* **Instagram**: `instagram.com/reel/xxx`, `instagram.com/p/xxx`, `instagram.com/stories/xxx`
* **Facebook**: `facebook.com/watch/?v=xxx`, `facebook.com/share/v/xxx`, `fb.watch/xxx`
* **X (Twitter)**: `x.com/usuario/status/xxx`, `twitter.com/usuario/status/xxx`




