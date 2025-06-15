# CodeVoxIA-
CodeVoxIA 
Proyecto de Texto a Voz: Escena de Diálogo

**Descripción**

Este proyecto genera una narración en audio a partir de un diálogo en español entre cuatro personajes (Mía, Zoe, Kai y el Profesor Vega) utilizando la biblioteca gTTS (Google Text-to-Speech) y pydub para procesar el audio. Cada personaje tiene una voz diferenciada mediante ajustes de velocidad y tono, simulando una conversación dinámica sobre un misterioso "glitch" en una red de realidad aumentada (AR). El resultado es un archivo de audio combinado (escena_completa.wav) que contiene todas las líneas del diálogo.

El proyecto incluye un script principal (text_to_speech.py) y un Jupyter Notebook (tts_experiments.ipynb) que documenta los experimentos iniciales con la biblioteca Coqui TTS antes de optar por gTTS como solución final debido a problemas con el soporte multilingüe y multi-speaker en Coqui TTS.

**Características**

Generación de audio a partir de texto en español usando gTTS.
Diferenciación de voces para cada personaje mediante ajustes de velocidad (slow) y cambio de tono (pitch_shift) con pydub.
Registro de logs para seguimiento del proceso y depuración de errores.
Creación automática de una carpeta audios/ para almacenar los archivos de audio generados.
Combinación de múltiples archivos de audio en un solo archivo final (escena_completa.wav).
Documentación de experimentos previos con Coqui TTS para explorar modelos avanzados de texto a voz.

**Estructura del Proyecto:**

tts_project/
├── audios/                     # Carpeta para los archivos de audio generados
├── scripts/
│   └── text_to_speech.py       # Script principal para generar los audios
├── notebooks/
│   └── tts_experiments.ipynb   # Jupyter Notebook con experimentos iniciales
├── requirements.txt            # Dependencias del proyecto
├── README.md                   # Documentación del proyecto
└── LICENSE                     # Licencia del proyecto (MIT)

**Requisitos**

**Software**

Python: Versión 3.8 o superior.
FFmpeg: Requerido por pydub para procesar archivos de audio.

**Dependencias de Python**

Las dependencias se encuentran en requirements.txt:

gTTS==2.5.3: Para generar audio a partir de texto.
pydub==0.25.1: Para procesar y combinar archivos de audio.


**Instalación**

Sigue estos pasos para configurar y ejecutar el proyecto en tu máquina:

**Clona el repositorio:**

git clone https://github.com/<tu-usuario>/tts_project.git
cd tts_project

**Crea y activa un entorno virtual (recomendado):**

python -m venv tts_env
source tts_env/bin/activate  # En Windows: tts_env\Scripts\activate

**Instala las dependencias:**

pip install -r requirements.txt

**Instala FFmpeg:**

**Windows:**

Descarga FFmpeg desde ffmpeg.org o usa un administrador de paquetes como Chocolatey:

choco install ffmpeg

Asegúrate de que ffmpeg esté en tu PATH. Puedes verificar ejecutando ffmpeg -version en la terminal.

**Linux/macOS:**

Instala FFmpeg con tu administrador de paquetes:

# Ubuntu/Debian
sudo apt-get install ffmpeg
# macOS (con Homebrew)
brew install ffmpeg

python --version
pip list

**Uso**
Ejecuta el script principal:

python scripts/text_to_speech.py

**Explora los experimentos:**

Abre el archivo notebooks/tts_experiments.ipynb en Jupyter Notebook para ver los intentos iniciales con Coqui TTS:

jupyter notebook notebooks/tts_experiments.ipynb

**Nota: Los experimentos con Coqui TTS requieren dependencias adicionales (como torch y TTS) que no están incluidas en requirements.txt para mantener el proyecto ligero.**

**Escucha el resultado:**

Reproduce el archivo audios/escena_completa.wav con cualquier reproductor de audio.

Desarrollo del Proyecto

**Fase 1: Experimentos con Coqui TTS**

Inicialmente, se exploró la biblioteca Coqui TTS para generar audios con modelos avanzados:

Modelo XTTS v2: Se intentó usar el modelo tts_models/multilingual/multi-dataset/xtts_v2 para generar voces multilingües y multi-speaker. Sin embargo, se encontraron errores relacionados con la falta del atributo speakers y problemas de compatibilidad con caracteres especiales en español (como ¡, ¿, á, etc.).

Modelo Tacotron2-DDC: Como alternativa, se probó el modelo tts_models/en/ljspeech/tacotron2-DDC, pero este no soportaba múltiples voces ni español, lo que resultó en audios con una sola voz en inglés y problemas con caracteres acentuados.

Estos experimentos están documentados en notebooks/tts_experiments.ipynb, donde se incluye el código para cargar modelos, parchear funciones de Coqui TTS, y generar audios de prueba.

**Fase 2: Implementación Final con gTTS**

Debido a las limitaciones de Coqui TTS, se optó por usar gTTS para generar audios en español. Para simular voces diferentes para cada personaje:

Se ajustó la velocidad (slow=True/False) en gTTS.

Se aplicaron cambios de tono (pitch_shift) usando pydub para diferenciar las voces de Mía, Zoe, Kai y el Profesor Vega.

Los audios individuales se combinan en un solo archivo WAV usando pydub.

El script final (text_to_speech.py) implementa esta solución, logrando una narración coherente con voces variadas.

Problemas Conocidos

**Coqui TTS:**

El modelo xtts_v2 no funcionó como se esperaba debido a errores con el atributo speakers y falta de soporte para caracteres especiales en español.
El modelo tacotron2-DDC solo soporta inglés y no maneja múltiples voces.

**gTTS:**

Requiere conexión a internet para generar audios, ya que utiliza los servidores de Google.

Las variaciones de voz son limitadas y se logran mediante ajustes de tono y velocidad, no con voces predefinidas como en Coqui TTS.

**FFmpeg:**

Debe estar instalado y en el PATH para que pydub funcione correctamente.

Contribuciones

**¡Las contribuciones son bienvenidas! Si deseas mejorar el proyecto, considera:**

Agregar soporte para otros idiomas o modelos TTS.

Mejorar la diferenciación de voces con técnicas avanzadas (por ejemplo, usando modelos locales de Coqui TTS).

Optimizar el procesamiento de audio para reducir el tiempo de generación.

Por favor, crea un pull request con tus cambios o abre un issue para discutir ideas.

Licencia

Este proyecto está licenciado bajo la Licencia MIT.

**Contactos:**

bilymrtz20@gmail.com
+18092494474

Para preguntas o sugerencias, contáctame a través de GitHub: .

Última actualización: 15 de junio de 2025
