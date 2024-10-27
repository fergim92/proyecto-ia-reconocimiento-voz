# Proyecto de Transcripción de Voz a Texto con IA

Este proyecto, desarrollado para la materia de Inteligencia Artificial en la **Universidad Nacional de Río Negro**, tiene como objetivo convertir la voz en texto utilizando modelos avanzados de IA como **Wav2Vec2**, y posteriormente realizar consultas sobre el texto transcrito utilizando el modelo de lenguaje **LLaMA 7B**, cuantizado a **4-bits** para reducir los requisitos de memoria. El sistema permite la transcripción de voz en tiempo real y genera respuestas inteligentes basadas en las consultas del usuario. 

Desarrollado por: Mauricio Boyé y Fernando Giménez.

## Características

- **Transcripción de voz a texto** con **Wav2Vec2**.
- **Consultas y generación de respuestas** utilizando **LLaMA 7B** cuantizado a 4-bits, ideal para dispositivos con **8 GB de RAM**.
- **Interfaz de usuario moderna** construida con **Next.js**.
- **Backend eficiente** desarrollado con **FastAPI**, que gestiona las consultas y la interacción con **LLaMA.cpp**.
- Preprocesamiento de audio antes de la transcripción.
- Despliegue fácil mediante **Docker**.

## Tecnologías Utilizadas

- **[Wav2Vec2](https://huggingface.co/models)**: Modelo para transcripción de voz a texto.
- **[LLaMA.cpp](https://github.com/ggerganov/llama.cpp)**: Implementación optimizada en **C++** de **LLaMA**, diseñada para ejecutarse en CPUs.
- **[FastAPI](https://fastapi.tiangolo.com/)**: Framework de backend en Python.
- **[Next.js](https://nextjs.org/)**: Framework de React para frontend.
- **[PyDub](https://github.com/jiaaro/pydub)**: Librería para preprocesamiento de audio.
- **[Docker](https://www.docker.com/)**: Plataforma de contenedores.

## Instalación y Configuración

### 1. Clonar el Repositorio

```bash
git clone https://github.com/fergim92/proyecto-ia-reconocimiento-voz
cd proyecto-ia-reconocimiento-voz
```

### 2. Configuración del Backend (FastAPI con LLaMA.cpp)

1. Instalar las dependencias de Python:
   ```bash
   pip install -r backend/requirements.txt
   ```

2. Descargar e instalar **LLaMA.cpp** y el modelo **LLaMA 7B** cuantizado:

   - Clonar el repositorio de **LLaMA.cpp**:
     ```bash
     git clone https://github.com/ggerganov/llama.cpp
     cd llama.cpp
     ```

   - Compilar **LLaMA.cpp**:
     ```bash
     make
     ```

   - Descargar el modelo **LLaMA 7B** (proporcionado por Meta):
     ```bash
     wget [URL_DEL_MODELO_LLAMA_7B]
     ```

   - Cuantizar el modelo a **4-bits** para reducir los requisitos de memoria:
     ```bash
     ./quantize modelo-original.bin modelo-cuantizado.bin 4
     ```

     Esto reduce el tamaño del modelo, haciéndolo adecuado para dispositivos con **8 GB de RAM**.

3. Configurar el backend para utilizar **LLaMA.cpp** con el modelo cuantizado. **FastAPI** llamará a **LLaMA.cpp** mediante `subprocess`:

   ```python
   from fastapi import FastAPI
   import subprocess

   app = FastAPI()

   @app.post("/llama_inference/")
   async def llama_inference(input_text: str):
       result = subprocess.run(['./llama.cpp', '--text', input_text], capture_output=True, text=True)
       return {"output": result.stdout}
   ```

4. Ejecutar el servidor de FastAPI:
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

Para desplegar el proyecto utilizando Docker:

```bash
docker-compose up --build
```

### 5. Uso de LLaMA.cpp con el modelo 7B cuantizado

- **LLaMA 7B cuantizado a 4-bits** se ejecuta directamente en **CPU**, lo que permite inferencias con bajo consumo de recursos. El tamaño del modelo se reduce a **3.5 GB** de RAM, ideal para sistemas con **8 GB de RAM**.
  
- El backend en **FastAPI** gestiona las consultas, las envía a **LLaMA.cpp** y devuelve las respuestas.

- Para mejorar el rendimiento, ajustar los parámetros del modelo en la configuración de **LLaMA.cpp**.

## Licencia

Este proyecto está licenciado bajo los términos de la licencia **MIT**.

