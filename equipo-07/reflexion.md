# reflexion.md - Análisis y Conclusiones del Proyecto

## 1. ¿Qué casos fallaron y por qué? ¿Qué cambiaron para corregirlos?
* **Falla inicial:** Al principio, el agente solicitaba constantemente el ID de la hoja de cálculo por chat antes de ejecutar la herramienta de escritura.
* **Causa:** No tenía fijo el nombre del documento dentro de las instrucciones del sistema ni en la herramienta.
* **Corrección:** Se añadió una directiva estricta en el *System Message* del Agente indicando el nombre exacto de la hoja (`Recepcion_Datos`) y se configuraron las descripciones de los campos mediante mapeo dinámico con los botones de IA (`✨`).

## 2. Una limitación del agente que no pudieron resolver
* La dependencia de la conectividad y de las cuotas de tasa de solicitudes (*Rate Limits / Error 429*) de la API gratuita de Gemini, lo cual puede generar intermitencias temporales si se realizan múltiples peticiones concurrentes de prueba en un lapso corto de tiempo.

## 3. ¿Qué cambiarían si este agente fuera a producción con usuarios reales?
* Se implementaría una base de datos relacional robusta (como PostgreSQL o Supabase) en lugar de Google Sheets para garantizar concurrencia y seguridad a escala.
* Se añadiría un canal de mensajería real (como WhatsApp Business API o Telegram) en lugar del chat interno de n8n.
* Se incorporaría un mecanismo avanzado de validación de entradas mediante esquemas estrictos (JSON Schema) para evitar errores tipográficos en fechas o IDs.

## 4. Qué hizo cada integrante, en concreto
* **Alan Jesús Aguilar Verdugo:** Desarrolló la estructura lógica del flujo en n8n, configuró los parámetros de LangChain, el modelo de chat de Gemini y resolvió la vinculación técnica de las herramientas de lectura y escritura en la nube.
* **Oscar Alejandro Bernal Petriz:** Diseñó la estructura de datos en Google Sheets, estructuró y documentó los 10 casos de prueba requeridos (`casos.csv`), y redactó los reportes de reflexión y arquitectura técnica.
