# 🎙️ LiveKit Voice AI Assistant

A real-time voice AI assistant built with **LiveKit Agents**, **Python**, and **Gradio**. The project provides a browser-based interface where users can connect their microphone, join a LiveKit room, and communicate with an AI voice assistant.

The application combines **speech-to-text**, **LLM-based responses**, **text-to-speech**, microphone visualization, and LiveKit real-time communication.

## ✨ Features

* 🎙️ Real-time voice conversation with an AI assistant
* 🔊 Speech-to-text using AssemblyAI
* 🧠 AI responses using Google Gemma
* 🗣️ Text-to-speech using Fish Audio
* 🎧 Real-time audio communication through LiveKit
* 🎤 Browser microphone permission and input handling
* 📊 Live microphone waveform visualizer
* 🔇 Mute and unmute microphone
* 🔊 Enable AI audio playback
* 🛑 Disconnect from the LiveKit room
* 🏠 Automatic unique room generation
* 👤 Custom user name support
* 🌐 Gradio-based web interface
* 🛡️ Environment-variable based LiveKit credentials
* 🎛️ AI voice processing with `ai-coustics`

## 🛠️ Technologies Used

* **Python 3.14**
* **LiveKit Agents**
* **LiveKit API**
* **Gradio**
* **AssemblyAI**
* **Google Gemma**
* **Fish Audio**
* **ai-coustics**
* **JavaScript**
* **HTML/CSS**
* **uv**
* **python-dotenv**

## 📁 Project Structure

```text
shah-zaib-arsh-livekit_agent/
│
├── README.md
├── agent.py
├── app.py
├── pyproject.toml
├── .python-version
│
└── src/
    └── livkit_agent/
        └── __init__.py
```

## ⚙️ Requirements

Before running the project, make sure you have:

* Python 3.14
* uv
* A LiveKit Cloud project
* LiveKit API Key
* LiveKit API Secret
* LiveKit WebSocket URL

## 🔐 Environment Variables

Create a `.env` file in the project root:

```env
LIVEKIT_URL=wss://your-livekit-project.livekit.cloud
LIVEKIT_API_KEY=your_livekit_api_key
LIVEKIT_API_SECRET=your_livekit_api_secret
```

Do not upload your `.env` file or expose your LiveKit API credentials on GitHub.

Add this to `.gitignore`:

```gitignore
.env
.venv/
__pycache__/
*.pyc
```

## 🚀 Installation

Clone the repository:

```bash
git clone https://github.com/shah-zaib-arsh/shah-zaib-arsh-livekit_agent.git
cd shah-zaib-arsh-livekit_agent
```

Create the virtual environment and install dependencies:

```bash
uv sync
```

Activate the environment on Windows CMD:

```cmd
.venv\Scripts\activate.bat
```

For PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

## ▶️ Run the Voice Agent

Start the LiveKit agent:

```bash
uv run agent.py dev
```

The agent connects to LiveKit and waits for users to join the configured room.

## 🌐 Run the Gradio Web Interface

Open another terminal and run:

```bash
uv run app.py
```

The Gradio application will be available at:

```text
http://127.0.0.1:7860
```

Open the address in your browser.

## 🎤 How It Works

```text
User
  │
  ▼
Gradio Web Interface
  │
  ▼
Create LiveKit Access Token
  │
  ▼
Join LiveKit Room
  │
  ├── Microphone Audio
  │        │
  │        ▼
  │   LiveKit Audio Stream
  │        │
  │        ▼
  │     AI Agent
  │
  └── AI Audio Response
           │
           ▼
      User's Browser
```

## 🧠 AI Agent Pipeline

The voice agent uses the following pipeline:

```text
Microphone
    ↓
LiveKit
    ↓
AssemblyAI Speech-to-Text
    ↓
Google Gemma LLM
    ↓
Fish Audio Text-to-Speech
    ↓
LiveKit
    ↓
User Speaker
```

## 🎙️ Assistant Behavior

The AI assistant is designed to be:

* Helpful
* Friendly
* Concise
* Informative
* Conversational

It avoids unnecessary complex formatting, emojis, asterisks, and excessive punctuation during voice responses.

## 🔊 Browser Audio

The web interface includes:

* Microphone permission handling
* Live microphone waveform
* Microphone mute/unmute controls
* AI audio playback activation
* Remote audio track handling
* Connection and disconnection status

The browser may ask for microphone permission when the **Connect** button is pressed.

## 🔧 Configuration

The LiveKit agent is configured in `agent.py`.

The web interface and LiveKit token generation are handled by `app.py`.

The project uses the LiveKit agent name:

```text
my-agent
```

Make sure the agent name used by the web application matches the agent configuration.

## 🔒 Security

Never commit sensitive credentials to GitHub.

Do not upload:

```text
.env
LIVEKIT_API_KEY
LIVEKIT_API_SECRET
```

Use environment variables instead.

## 📌 Future Improvements

Possible improvements for the project include:

* Conversation history
* User authentication
* Multiple AI personalities
* Voice selection
* Better error handling
* Chat transcript display
* Mobile-friendly voice controls
* Deployment to a public server
* Additional AI models
* Persistent conversation storage

## 👨‍💻 Author

**Muhammad Shahzaib**

GitHub:
https://github.com/shah-zaib-arsh

LinkedIn:
https://www.linkedin.com/in/muhammad-shahzaib-arshed/

## 📄 License

This project is created for learning, experimentation, and educational purposes.

---

⭐ If you find this project useful, consider giving the repository a star.
