<p align="center">
  <img src="docs/img/banner.png" alt="Shotlight: busca en todas tus capturas, por lo que dicen o por lo que muestran" width="100%">
</p>

<p align="center">
  <b>Busca en todas las capturas de pantalla que has hecho, por lo que dicen o por lo que muestran.</b><br>
  Local y privado. Más de 50 idiomas. Búsqueda visual. Hecho para ti <i>y</i> para tus asistentes de IA.
</p>

<p align="center"><a href="README.md">English</a> · Español</p>

Shotlight lee el texto de cada captura que tomas y lo vuelve buscable. Pulsas un atajo, escribes unas letras de algo que recuerdas haber visto y todas las capturas que coinciden se iluminan, con las palabras brillando en su sitio. También entiende lo que una captura *muestra* («atardecer», «gráfico de barras», «un gato»), saca lo que normalmente quieres copiar (códigos de verificación, enlaces, montos) y mantiene tus secretos fuera de la vista.

Todo ocurre en tu ordenador. Sin cuenta, sin nube y sin telemetría.

<p align="center">
  <img src="docs/img/search-light.png" alt="Buscar 'codigo' encuentra 'código' en un SMS, con el código listo para copiar" width="92%">
</p>

## Qué hace

- **Encuentra cualquier palabra que viste**, mientras escribes, en milisegundos. Da igual acentos y mayúsculas: `codigo` encuentra `Código`, `munoz` encuentra `Muñoz`.
- **Perdona errores**, tuyos y del OCR: `reserba` encuentra `Reserva` como *coincidencia cercana*, siempre marcada y siempre después de las exactas.
- **Encuentra lo que no sabes escribir**: la búsqueda visual (opcional) encuentra capturas por lo que muestran, en español: `atardecer en la montaña` encuentra una foto sin una sola palabra.
- **Te da lo útil**: códigos de un solo uso, enlaces, correos, teléfonos, montos, IPs y colores aparecen como chips que copias sin abrir la captura.
- **Se ordena sola**: códigos, compras, errores, programación, chats, viajes, documentos; cada captura recibe un título legible y las ráfagas casi idénticas se agrupan.
- **Guarda tus secretos**: detecta claves de API, tokens, tarjetas y contraseñas; esas capturas se difuminan, los valores se ocultan y nunca se entregan a una IA mientras el escudo de privacidad esté activo.
- **Tu IA puede buscar en tus capturas** con el servidor [MCP](https://modelcontextprotocol.io) integrado (Claude, Cursor y cualquier cliente MCP).
- **Lee como tú**: columna por columna, capturas largas en mosaicos a resolución completa, y las capturas movidas o renombradas conservan su texto sin volver a leerse.
- **Selecciona texto sobre la imagen** o arrastra un recuadro para copiar solo esas líneas.
- **Limpia**: sugiere qué tirar (códigos viejos, duplicados, capturas con secretos) y lo manda a la papelera con opción de deshacer.

## Descargar

**[Descargar Shotlight para Windows](https://github.com/morningstar-code/shotlight/releases/latest)** (Windows 10 y 11, 64 bits, unos 126 MB, gratis).

1. Descomprímelo y mueve la carpeta **Shotlight** a un lugar fijo, por ejemplo `%LOCALAPPDATA%\Programs\Shotlight`.
2. Abre **Shotlight.exe**. Windows puede avisar de un editor desconocido porque la app aún no está firmada: elige *Más información* y luego *Ejecutar de todas formas*.
3. Elige las carpetas donde guardas tus capturas. Empieza a leer enseguida, de la más reciente a la más antigua, y puedes buscar mientras lee.

Pulsa **Alt+Shift+H** en cualquier parte para abrir o cerrar la búsqueda. Shotlight vive en el área de notificación y no ocupa la barra de tareas. *Iniciar con el sistema* en Ajustes mantiene las capturas nuevas al día. Para actualizar, sal desde su icono y reemplaza la carpeta por la nueva; el índice y los ajustes se conservan. Aún no hay versión para macOS ni Linux.

## Buscar

| Escribes | Obtienes |
|---|---|
| `factura marzo` | Capturas con ambas palabras, en cualquier línea |
| `"pedido confirmado"` | Esa frase exacta |
| `codigo -whatsapp` | Excluye capturas que mencionen una palabra |
| `en:discord` | Solo una carpeta |
| `fecha:hoy` `fecha:ayer` `fecha:semana` `fecha:2026-10` `fecha:lunes` | Un día, un mes, un año, o los últimos 7 / 30 / 365 días |
| `antes:2026-08` `despues:2026-01-15` | Antes o después de una fecha |
| `tipo:codigo` `tipo:factura` `tipo:error` `tipo:chat` `tipo:viaje` `tipo:privado` | Un tipo de captura |
| `tiene:enlace` `tiene:correo` `tiene:tel` `tiene:dinero` `tiene:secreto` | Capturas con un tipo de valor |
| `sort:old` | Las más antiguas primero |

Los filtros en inglés (`in:`, `date:`, `is:`, `has:`) también funcionan.

## Para asistentes de IA (MCP)

```sh
claude mcp add shotlight -- "%LOCALAPPDATA%\Programs\Shotlight\shotlight-cli.exe" mcp
```

Usa la carpeta donde pusiste Shotlight. Para Claude Desktop, Cursor y otros, `shotlight-cli.exe mcp-config` imprime el JSON, y Ajustes → Asistentes de IA lo muestra listo para copiar. Herramientas: `search_screenshots`, `get_screenshot`, `recent_screenshots`, `find_values` (por ejemplo, el último código de verificación) e `index_status`.

## Privacidad

Sin telemetría, sin cuentas, sin buscar actualizaciones (y con la telemetría de ONNX Runtime desactivada). Los modelos de lectura vienen incluidos, así que no se descarga nada; solo se descargan los que actives tú (una escritura extra o la búsqueda visual), con versión fija y comprobación SHA-256. Tus capturas y su texto nunca salen de tu ordenador, salvo lo que tú decidas darle a un asistente de IA por MCP. Shotlight nunca modifica ni borra una captura salvo que tú la mandes a la papelera.

## Comparado con gyotaku

Shotlight es una reinterpretación de [gyotaku](https://github.com/xevrion/gyotaku) de [@xevrion](https://github.com/xevrion), cuya idea inspiró este proyecto. No comparten código: es una implementación independiente. La tabla completa está en el [README en inglés](README.md#compared-with-gyotaku). En resumen: Shotlight añade búsqueda visual multilingüe, títulos y tipos automáticos, más escrituras, captura del portapapeles en Windows, chips para copiar, escudo de privacidad, servidor MCP, limpieza e interfaz en español; gyotaku es nativo (Rust + GPUI), usa mucha menos memoria y tiene instaladores para Linux, macOS y Windows.

## El nombre

**Shotlight** es un foco de luz para tus capturas: esperan a oscuras y, al escribir, las palabras que buscas se encienden como luciérnagas en una noche de verano. El logo es una lupa cuyo mango es la estela de una luciérnaga, dentro de las esquinas de una captura.

## Licencia

Shotlight es **gratis**, para uso personal y comercial, pero no es de código abierto: mira [LICENSE](LICENSE). Usa componentes de código abierto, listados con sus licencias en [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

Ideas y fallos: en [issues](https://github.com/morningstar-code/shotlight/issues).
