# Guía de Actualización de Firmware - Serie ECHO

## 1. Introducción
Este repositorio contiene la herramienta RKDevelopTool y los controladores necesarios para instalar actualizaciones de firmware en los dispositivos de la serie Snowsky ECHO.

### Referencia de Archivos de Firmware
Asegúrate de usar el archivo `.img` correcto para tu modelo específico:
*   **ECHO:** `HT9099(ECHO)BT53_HW_V1.7_SW_V1.2.0_HIFIDAC43198_6KEY_20260204_1130`
*   **Echo Mini (versión 8GB):** `HT9093BT53_五套UI_HW_V1.3_SW_V3.2.0_HIFIDAC43131_LCD读ID识别_6KEY_20260211_1043`
*   **Echo Mini (versión 512MB):** `NANO_F512M_HW_V1.0_SW_V1.5.0_HIFIDAC43131_3KEY_20260714_1725`
*   **Echo Nano:** `NANO_F512M_HW_V1.0_SW_V1.4.0_HIFIDAC43131_3KEY_20260623_1024`

## 2. Instalar el Controlador (Driver)
Antes de usar la herramienta, debes instalar el controlador Rockusb en tu computadora:
1. Conecta el dispositivo a la PC.
2. Haz clic derecho en **"Este equipo"** (o "Mi PC") → selecciona **"Propiedades"** → selecciona **"Administrador de dispositivos"**.
3. Despliega **"Otros dispositivos"** y busca el dispositivo desconocido con un signo de exclamación amarillo.
4. Haz clic derecho sobre él y selecciona **"Actualizar controlador"**.
5. Sigue las instrucciones, elige la instalación manual y selecciona la carpeta `Driver` (o la carpeta `Rockusb`) dentro del directorio de esta herramienta.
6. Selecciona el controlador correspondiente según tu sistema (x86/x64, Win7/Win10).
*Nota: Si el controlador de Win10 falla, puedes intentar instalar el controlador de Win8.*

## 3. Flashear el Firmware
1. Abre el programa **`RKDevelopTool.exe`**. *(Nota: La herramienta ya ha sido configurada en inglés cambiando `Selected=2` en el archivo `config.ini`).*
2. Haz clic en **"Load firmware"** (botón 1) y selecciona el archivo `.img` correcto para tu dispositivo de la lista anterior. La herramienta mostrará `Loading firmware...` y luego `Loading firmware Finished.`.
3. Presta atención a la esquina inferior izquierda del programa. Debería mostrar **"Found one MSC device"**.
4. Haz clic en el botón **"Switch"** (botón 2 para cambiar de modo).
   * Si el controlador se instaló correctamente, la esquina inferior izquierda cambiará a **"Found one MASKROM device"** o **"Found one Loader device"** (cualquiera está bien).
   * *Solución de problemas:* Si muestra "No devices found", la instalación del controlador falló. El dispositivo se apagará y no se conectará. Reinstala el controlador, luego reinicia el dispositivo manteniendo presionado el botón de Reset y volviendo a encenderlo.
5. Haz clic en **"Erase system block"** (botón 3) para borrar el firmware antiguo. *(Importante hacer esto antes de actualizar).*
6. Haz clic en **"Upgrade"** (botón 5) para instalar el nuevo firmware.
7. Los datos en la esquina inferior derecha mostrarán el progreso. Una vez completado, dirá: `Download Firmware Success`.

## 4. Descripción de Mensajes de Error
*   **"Failed to load configuration information..."** — Error al cargar `config.ini`. Generalmente ocurre si la carpeta tiene caracteres chinos o especiales (Este repositorio soluciona ese problema).
*   **"Failed to load firmware..."** — No se seleccionó el firmware o el archivo es ilegible.
*   **"Another operation is in progress, please wait!"** — Espera a que termine la tarea actual.
*   **"Operation mismatch..."** — Asegúrate de que el chip soportado coincida con la pestaña seleccionada.
*   **"No device found..."** — Verifica que el dispositivo esté conectado y en estado Rockusb.
*   **"Multiple devices found..."** — Mantén solo un dispositivo conectado a la PC.
*   **"Failed to obtain device information..."** — Desconecta y vuelve a conectar el dispositivo.
*   **"Unsupported device type..."** — El dispositivo debe estar en estado Rockusb, no en modo de almacenamiento (MSC). Asegúrate de hacer clic en "Switch" primero.

## 5. Notas Importantes
*   Si el proceso se queda atascado en *"Download Boot Start"*, por favor desconecta el dispositivo y reinicia el proceso de actualización.
*   En sistemas Windows Vista o Windows 7, el programa debe ejecutarse con privilegios de administrador.
