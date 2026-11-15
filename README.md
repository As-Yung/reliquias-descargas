# Reliquias del Alma: descargas

Descargas oficiales del juego. Cuando lo tienes instalado, se actualiza solo.

- **PC (Windows):** [Reliquias-del-Alma-Setup.exe](https://github.com/As-Yung/reliquias-descargas/releases/latest/download/Reliquias-del-Alma-Setup.exe)
- **Android:** [Reliquias-del-Alma-Android.apk](https://github.com/As-Yung/reliquias-descargas/releases/latest/download/Reliquias-del-Alma-Android.apk)
- **Batocera (Raspberry Pi):** [Reliquias-del-Alma-Batocera.zip](https://github.com/As-Yung/reliquias-descargas/releases/latest/download/Reliquias-del-Alma-Batocera.zip)

## Cómo se publica

El flujo [`publicar.yml`](.github/workflows/publicar.yml) compila el juego a partir de su código, que está en un repo privado. Corre en este repo público porque aquí GitHub Actions no gasta minutos.

- Cada 30 minutos mira si hay una versión nueva del juego y, si la hay, la publica sola.
- También se puede lanzar a mano: **Actions → Publicar el juego → Run workflow**.

El flujo necesita estos secretos, en **Settings → Secrets and variables → Actions**:

| Secreto               | Qué es                                                                          |
| --------------------- | ------------------------------------------------------------------------------- |
| `CODIGO_TOKEN`        | Llave de solo lectura (fine-grained) del repo del juego: _Contents: Read-only_. |
| `ANDROID_FIRMA`       | Llave de firma de Android en base64 (la misma del repo del juego).              |
| `ANDROID_FIRMA_CLAVE` | Contraseña de esa llave.                                                        |

Los secretos nunca se muestran en los registros. Si falta alguno, no se publica nada.

GitHub apaga los flujos programados de un repo público tras 60 días sin commits. Si pasa, vuelve a activarlo en **Actions → Publicar el juego → Enable workflow**.
