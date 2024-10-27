# Proyecto de Transcripción de Voz a Texto con IA

Este proyecto es parte de la materia de Inteligencia Artificial en la **Universidad Nacional de Río Negro**. Su objetivo principal es convertir la voz en texto utilizando modelos avanzados de IA, como **Wav2Vec2**, para luego realizar consultas sobre ese texto con un modelo de lenguaje grande, como **LLaMA**. El sistema permite transcribir la voz en tiempo real y generar respuestas inteligentes basadas en las consultas del usuario. Realizado por Maurico Boyé y Fernando Giménez.

## Características

- **Transcripción de voz a texto** utilizando el modelo **Wav2Vec2**.
- **Consultas y generación de respuestas** mediante el modelo **LLaMA**.
- **Interfaz de usuario moderna** construida con **Next.js**.
- **Backend rápido y eficiente** usando **FastAPI**.
- Soporte para preprocesamiento de archivos de audio antes de la transcripción.
- Fácil despliegue usando **Docker**.

## Tecnologías Utilizadas

- **[Wav2Vec2](https://huggingface.co/models)**: Modelo avanzado de transcripción de voz a texto.
- **[LLaMA](https://ai.facebook.com/blog/large-language-model-meta-ai/)**: Modelo de lenguaje grande para consultas de IA.
- **[FastAPI](https://fastapi.tiangolo.com/)**: Framework de backend asíncrono.
- **[Next.js](https://nextjs.org/)**: Framework de React para frontend.
- **[PyDub](https://github.com/jiaaro/pydub)**: Herramienta para preprocesamiento de audio.
- **[Docker](https://www.docker.com/)**: Plataforma de contenedores para el despliegue del proyecto.

## Instalación y Configuración

Sigue los siguientes pasos para configurar el entorno de desarrollo y ejecutar el proyecto en tu máquina local.

### 1. Clonar el Repositorio

```bash
https://github.com/fergim92/proyecto-ia-reconocimiento-voz
cd proyecto-ia-reconocimiento-voz
```

### 2. Configuración del Backend (FastAPI)

1. Instalar las dependencias de Python:
   ```bash
   pip install -r backend/requirements.txt
   ```

2. Ejecutar el servidor de FastAPI:
   ```bash
   uvicorn backend.main:app --reload
   ```

### 3. Configuración del Frontend (Next.js)

1. Instalar las dependencias de Next.js:
   ```bash
   cd frontend
   npm install
   ```

2. Ejecutar el servidor de desarrollo:
   ```bash
   npm run dev
   ```

### 4. Configuración de Docker (Opcional)

Para desplegar el proyecto utilizando Docker, puedes construir la imagen y ejecutar los contenedores:

```bash
docker-compose up --build
```

## Licencia

Este proyecto está licenciado bajo los términos de la licencia **MIT**.
