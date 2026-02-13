Notebook 1 — ¿Por qué usar unstructured-client?
Problema

Instalar el paquete completo unstructured genera:

Conflictos de dependencias

Problemas en Docker

Configuración compleja (poppler, tesseract, etc.)

Errores frecuentes en Windows y WSL

Decisión Técnica

En lugar de usar:

pip install unstructured


Se optó por:

pip install unstructured-client
pip install langchain-unstructured

Ventajas

✔ Instalación limpia
✔ Arquitectura desacoplada
✔ Procesamiento vía API
✔ Ideal para entornos productivos

Este notebook demuestra pruebas, errores encontrados y comparación técnica.

Notebook 2 — Implementación de RAG Tradicional

En este notebook se construye el pipeline base:

Carga de PDF

Extracción de texto

Chunking

Embeddings

Vector Store

Retrieval + LLM

Limitaciones detectadas

No entiende imágenes

No interpreta gráficos

No procesa tablas complejas

Este notebook sirve como línea base arquitectónica.

Notebook 3 — Migración a RAG Multimodal

Aquí ocurre la transformación principal del proyecto.

Cambios implementados
🔹 Reemplazo del Loader
from langchain_unstructured import UnstructuredLoader

🔹 Procesamiento de imágenes

Extracción de imágenes

Conversión a base64

Envío a modelo multimodal

Generación de resumen textual

🔹 Uso de modelo multimodal

Se utiliza GPT-4o para generar descripciones de imágenes que luego se indexan junto al texto.

Esto permite consultas como:

¿Qué muestra el gráfico financiero de la página 5?

Notebook 4 — Comparación Antes vs Después

Este notebook documenta:

Cambios en dependencias

Cambios en arquitectura

Cambios en pipeline

Mejora en capacidad de respuesta

Arquitectura Final

RAG Multimodal:

Usuario
↓
Notebook Backend (Pipeline IA)
↓
Unstructured API
↓
Vector Store (ChromaDB)
↓
LLM Multimodal
