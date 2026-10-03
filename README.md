# Conversational-AI-Agent
Prueba de concepto: Agente Inteligente con arquitectura RAG para asesoría financiera.


# Conversational AI Agent - Proof of Concept (PoC)

## Descripción del Proyecto
Este repositorio contiene una Prueba de Concepto (PoC) de un Agente de Inteligencia Artificial Conversacional diseñado para el sector bancario. El objetivo principal es demostrar la viabilidad técnica de orquestar múltiples fuentes de datos (estructuradas y no estructuradas) mediante un modelo de lenguaje de última generación, permitiendo al usuario realizar consultas financieras cruzadas en lenguaje natural.

## Arquitectura Técnica
El agente fue construido en Python y orquestado utilizando la API de *Interactions* (Stateful) de Google GenAI, superando los desafíos de las firmas de razonamiento en modelos avanzados. La arquitectura integra:

1. **Tool Calling (Enrutamiento Inteligente):** El agente evalúa la intención del usuario y decide dinámicamente qué herramienta ejecutar (SQL o RAG).
2. **Retrieval-Augmented Generation (RAG):** Motor de búsqueda semántica basado en embeddings (`gemini-embedding-2`) acoplado a la métrica de Similitud del Coseno para consultar políticas de productos alojadas externamente, previniendo alucinaciones.
3. **Integración SQL:** Conexión a una base de datos relacional (SQLite) para extraer, filtrar y calcular datos transaccionales de los clientes en tiempo real.
4. **Context Management:** Manejo automático del estado y contexto de la conversación (memoria) directamente en el servidor.
5. **Fallback & Error Handling:** Trazabilidad (logs) y manejo de excepciones en la ejecución de las *Tools* para garantizar una experiencia de usuario fluida incluso ante fallos de red o de infraestructura.

## Stack Tecnológico
* **Lenguaje:** Python
* **LLM Core:** `gemini-3.5-flash` (Google GenAI SDK - API Interactions)
* **Embeddings:** `gemini-embedding-2`
* **Base de Datos:** SQLite / Pandas
* **Búsqueda Semántica:** Numpy 
* **Entorno de Desarrollo:** Google Colab / GitHub REST API

## 🚀 Potencial de Escalabilidad (Roadmap a Producción)
Aunque este código está diseñado como un prototipo funcional, la arquitectura propuesta es agnóstica y escalable a un entorno Enterprise:
* **LLMOps / MLOps:** Transición del prototipo a plataformas como AWS Bedrock o Amazon SageMaker.
* **Vector Store:** Migración de la búsqueda matricial local a bases de datos vectoriales dedicadas (ChromaDB, Pinecone, o AWS OpenSearch) para manejar millones de tokens.
* **Data Lake:** Conexión de la herramienta SQL hacia un Data Warehouse corporativo (ej. Snowflake o AWS Redshift).
