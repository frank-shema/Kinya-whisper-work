🗣️ KinyaWhisper – Kinyarwanda Voice Assistant
A lightweight, voice-enabled assistant that understands and responds in Kinyarwanda, simulating humanoid robot voice interaction. Built for the Intelligent Robotics course at Rwanda Coding Academy, this project leverages Automatic Speech Recognition (ASR), Natural Language Processing (NLP), and Text-to-Speech (TTS) to create an AI-powered assistant tailored for Kinyarwanda speakers.

🎯 Project Overview
KinyaWhisper is designed to:

🎤 Transcribe Kinyarwanda speech using a fine-tuned OpenAI Whisper model.
🧠 Understand questions via rule-based NLP with fuzzy matching.
🗣️ Respond in Kinyarwanda using offline TTS (pyttsx3).

This project demonstrates the potential of localized AI for voice interaction in underrepresented languages like Kinyarwanda.

📁 Project Structure
.
├── audio/ # Custom Kinyarwanda audio samples (44 WAV files)
├── dataset.jsonl # Metadata for training (audio paths + transcriptions)
├── kinya-whisper-model/ # Fine-tuned Whisper model
├── train.py # Script for fine-tuning Whisper
├── inference.py # Script for batch transcription
├── main.py # Batch-mode voice assistant (ASR + NLP + TTS)
├── bach_main.py # CLI for live audio recording and response
├── transcriptions.txt # Output transcriptions from inference
├── README.md # Project documentation

🚀 Features

ASR: Converts Kinyarwanda speech to text using a fine-tuned Whisper model.
NLP: Matches transcribed text to predefined answers using fuzzy logic (difflib).
TTS: Generates spoken responses in Kinyarwanda via pyttsx3.
Live Recording: Supports real-time voice input via microphone (bach_main.py).
Batch Processing: Processes multiple audio files for transcription and response (main.py).

🛠️ Technologies

Python 3.10+
OpenAI Whisper (fine-tuned whisper-small)
Transformers (Hugging Face)
Torchaudio for audio processing
Pyttsx3 for offline TTS
Sounddevice for live microphone input
Difflib for fuzzy text matching

🧠 Model Training

Dataset: 44 custom Kinyarwanda audio samples created with BearAudioTool.
Base Model: openai/whisper-small
Fine-Tuning:
1st phase: 40 epochs
2nd phase: 20 additional epochs
3rd phase: 10 final epochs

Performance: Good to generous transcription accuracy across all 44 test samples.

📌 Setup and Installation
Prerequisites

Python 3.10+
Git
Microphone (for live recording)

Steps

Clone the Repository:
git clone https://github.com/hrh2/kinyawhisper-voice-assistant.git
cd kinyawhisper-voice-assistant

Install Dependencies:
pip install transformers[torch] datasets torchaudio pyttsx3 sounddevice

▶️ How to Run

1. Batch Mode (Process Audio Files)
   Run the main script to transcribe all .wav files in the audio/ folder, match them to answers, and speak responses:
   python main.py

2. Live Recording Mode (CLI)
   Run the CLI script to record live audio, transcribe it, and respond:

For first-time setup, uncomment line 66 in bach_main.py:# model = WhisperForConditionalGeneration.from_pretrained("openai/whisper-small") #first time

Comment out the fine-tuned model line:model = WhisperForConditionalGeneration.from_pretrained("./kinya-whisper-model")

Run:python bach_main.py

3. Run Inference Only
   Transcribe audio files without NLP or TTS:
   python inference.py

4. Train the Model (Optional)
   Fine-tune the Whisper model using the provided dataset:
   python train.py

🗣️ Sample Commands and Responses

Kinyarwanda Question
Response

amakuru yawe
Ni meza, urakoze! nkufashe iki?

witwa nde
Nitwa Mudasa AI.

uzi ikinyarwanda
Nkunda gufasha abantu mu rurimi rwacu.

wiriwe
Wiriwe neza.

umworozi ni iki
Umworozi ni umuntu utunga amatungo.

Fuzzy matching ensures robustness for partial or mispronounced inputs.

🧪 Testing with Audio

Batch Mode: Place .wav files in the audio/ folder (e.g., muraho.wav, inzovu.wav).
Live Mode: Speak directly into the microphone when prompted by bach_main.py.
Example commands: muraho, umwana, vuga gahoro, kwandika.

🎓 Academic Context

Course: Intelligent Robotics
Institution: Rwanda Coding Academy
Instructor: Gabriel Baziramwabo
Assignment: Term 3, Assignment 1 (Due April 30, 2025)

👤 Author
HIRWA Rukundo Hope

Email: gakundohope5@gmail.com  
GitHub: @hrh2

📝 License
This project is licensed under the MIT License. See the LICENSE file for details.

🙌 Acknowledgments

OpenAI for the Whisper model
Hugging Face for Transformers and datasets
Rwanda Coding Academy for the opportunity to explore AI in local languages
