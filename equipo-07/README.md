# README.md - Agente de Recepción Virtual con n8n y Gemini

## 1. Integrantes y Rol
* **Alan Jesús Aguilar Verdugo (Matrícula: 24040737)**: Arquitectura del flujo en n8n, configuración de la API de Google Gemini y diseño de la lógica de herramientas (Tools).
* **Oscar Alejandro Bernal Petriz (Matrícula: 24040484)**: Diseño de base de datos en Google Sheets (`Recepcion_Datos`), estructuración de casos de prueba y validación de restricciones (Guardrails).

## 2. Escenario Elegido y Problema que Resuelve
El proyecto implementa un **Agente de Recepción Virtual Automatizado** diseñado para gestionar la atención a clientes, registro de citas y consulta de servicios en una base de datos centralizada. Resuelve la saturación de los canales de atención tradicionales y automatiza el registro de datos operativos sin intervención manual, reduciendo errores humanos en la captura de información.

## 3. Diagrama o Captura del Workflow
*(Incluir captura del flujo completo de n8n mostrando el AI Agent, Model, Memory y las herramientas de Google Sheets).*

## 4. Tabla de Herramientas (Tools)

| Nombre de la Tool | Qué hace | Cuándo debería usarla el agente | Tipo (Lectura / Escritura) |
| :--- | :--- | :--- | :--- |
| **Get Row(s)** | Consulta registros existentes en la hoja de Google Sheets. | Cuando el usuario solicita información sobre un cliente, cita o servicio previamente registrado. | **Lectura** |
| **Append Row** | Inserta una nueva fila con los datos de una cita o servicio. | Cuando el usuario proporciona explícitamente los datos para dar de alta un nuevo registro. | **Escritura** |

## 5. Stack Elegido por Capa y Por Qué
* **Orquestación y Automatización:** n8n (Permite un desarrollo ágil basado en nodos visuales y soporte nativo para agentes LangChain).
* **Modelo de Inteligencia Artificial:** Google Gemini (1.5 Flash) a través de Google AI Studio (Ofrece alta velocidad de respuesta, procesamiento multimodal y estabilidad en el nivel gratuito).
* **Base de Datos / Almacenamiento:** Google Sheets (`Recepcion_Datos`) (Solución en la nube accesible, ligera y con integración directa mediante credenciales OAuth/API).

## 6. Cómo Ponerlo a Funcionar
1. **Credenciales necesarias:** 
   * Cuenta de Google AI Studio / Gemini API Key.
   * Credenciales de Google Sheets conectadas en n8n.
2. **Datos a Cargar:** 
   * Una hoja de cálculo en Google Drive denominada `Recepcion_Datos` con las columnas: `ID`, `CLIENTE`, `SERVICIO`, `FECHA`, `ESTADO`.
3. **Importación:** Importar el archivo `workflows/01-agente.json` en su instancia de n8n, verificar las credenciales y activar el nodo de chat.