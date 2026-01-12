AI Multilingual Speech-to-Speech Translation System

An end-to-end AI-powered Speech-to-Speech Translation system that converts spoken input (audio, video, microphone, or YouTube URL) into translated text and synthesized speech across multiple Indian languages.

📌 Project Overview

This project implements a complete Automatic Speech Recognition (ASR) → Neural Machine Translation (NMT) → Text-to-Speech (TTS) pipeline using modern deep learning models. It supports English and Hindi speech input and translates the content into 12+ Indian languages, producing both translated text and corresponding speech output.

The system is designed with a modular backend architecture, an interactive OTT-style web interface, and robust audio preprocessing, making it suitable for real-world multilingual and multimedia applications.

Datasets Used english-https://www.kaggle.com/datasets/mozillaorg/common-voice hindi-https://huggingface.co/datasets/ai4bharat/Lahaja

🔁 Important Note on ASR Model Usage

⚠️ The ASR model was fine-tuned locally and is not included in this repository due to size and environment constraints.

To ensure reproducibility and ease of use, the repository supports execution using a public pretrained Whisper model, while retaining compatibility with the locally trained model.

🧠 ASR Model Configuration Options ✅ Option 1: Use Public Whisper Model (Recommended)

Edit the file:

backend/services/asr/whisper_service.py

Set:

MODEL_PATH = "openai/whisper-tiny"

This option allows immediate execution without requiring any local model files.

✅ Option 2: Use Fine-Tuned Local Whisper Model (Advanced)

If access to the trained model is available:

Place the model directory at:

models/whisper_tiny_stage2/

Ensure it contains standard Hugging Face files:

config.json model.safetensors tokenizer_config.json vocab.json

Keep:

MODEL_PATH = "models/whisper_tiny_stage2"

⚠️ This option is intended for local execution only.

🧠 System Architecture

Input Sources

Audio file upload

Video file upload

Microphone recording

YouTube URL

Processing Pipeline

Audio extraction and normalization (16 kHz, mono)

Automatic Speech Recognition (Whisper ASR)

Multilingual Translation (NLLB-200)

Text-to-Speech synthesis (Edge TTS)

Caption generation and audio playback

🔧 Technologies Used Core AI Models

Whisper-Tiny — Automatic Speech Recognition

NLLB-200 (Distilled 600M) — Multilingual Translation

Edge TTS — Text-to-Speech synthesis

Libraries & Tools

PyTorch

Hugging Face Transformers

Librosa

FFmpeg

yt-dlp

Flask

HTML, CSS, JavaScript

🌍 Supported Output Languages

Tamil, Hindi, Telugu, Malayalam, Kannada, Bengali, Gujarati, Marathi, Punjabi, Urdu, Odia, Assamese

🧪 Model Training & Evaluation ASR Training Details

Base model: Whisper-Tiny

Fine-tuned locally on an English–Hindi dataset (70:30)

Audio standardized to 16 kHz mono

Chunk-based inference implemented for long-duration audio

Evaluation Metrics

Word Error Rate (WER)

Character Error Rate (CER)

Observed Results

English WER ≈ 11.7%

Hindi WER ≈ 57.3%

Hindi CER ≈ 7.29%

🖥️ User Interface Features

OTT-style interactive interface

Separate controls for Audio, Video, Microphone, and YouTube URL

Language selection dropdown

Real-time processing status updates

Caption display

Translated audio playback with download option

📁 Project Structure speech-translation-system/ │ ├── backend/ │ ├── api/ │ ├── pipeline/ │ ├── services/ │ │ ├── asr/ │ │ ├── translation/ │ │ ├── tts/ │ │ └── video/ │ ├── static/ │ ├── templates/ │ └── websocket/ │ ├── models/ │ └── whisper_tiny_stage2/ # optional local model │ ├── docs/ ├── requirements.txt ├── README.md

▶️ How to Run Locally git clone https://github.com/varshan2004/ai-speech-translator.git cd ai-speech-translator python -m venv venv venv\Scripts\activate # Windows pip install -r requirements.txt python -m backend.api.app

Open in browser:

http://127.0.0.1:5000

⚠️ Known Limitations

Free cloud tiers are insufficient due to transformer model memory requirements

Long audio processing is slower on CPU-only systems

ASR accuracy depends on audio quality and accent variability

🚀 Future Enhancements

GPU-accelerated deployment

Real-time streaming transcription

Speaker diarization

Improved Hindi ASR accuracy

Scalable cloud-native deployment

📜 License

MIT License

👨‍💻 Project Context

Developed as part of an Applied AI / ML Project Experience under Infosys Springboard.
