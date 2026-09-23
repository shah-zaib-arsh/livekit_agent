# 🎙️ LiveKit Voice AI Assistant

A real-time voice AI assistant built with **LiveKit Agents**, **Python**, and **Gradio**.

This project provides a browser-based voice interface where users can connect their microphone, join a LiveKit room, and talk with an AI voice assistant in real time.

The application combines speech-to-text, an LLM, text-to-speech, LiveKit real-time communication, microphone visualization, and browser audio controls.

---

## ✨ Features

* 🎙️ Real-time voice conversation
* 🔊 Speech-to-text using AssemblyAI
* 🧠 AI responses using Google Gemma
* 🗣️ Text-to-speech using Fish Audio
* 🎧 Real-time audio communication through LiveKit
* 🎤 Browser microphone support
* 📊 Live microphone waveform visualizer
* 🔇 Mute and unmute microphone
* 🔊 AI audio playback control
* 🛑 Disconnect from LiveKit room
* 🏠 Automatic unique room generation
* 👤 Custom user name
* 🌐 Gradio web interface
* 🛡️ Environment-variable based credentials
* 🎛️ AI audio enhancement using ai-coustics

---

# 🛠️ Technologies Used

* Python 3.14
* LiveKit Agents
* LiveKit API
* LiveKit Inference
* Gradio
* AssemblyAI
* Google Gemma
* Fish Audio
* ai-coustics
* JavaScript
* HTML
* CSS
* uv
* python-dotenv

LiveKit Inference provides access to supported STT, LLM, and TTS providers through LiveKit Cloud without requiring separate provider plugins for the models used in this project.

---

# 📁 Project Structure

```text
livekit_agent/
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

---

# ✅ Requirements

Before running the project, install the following:

* Python 3.14
* uv
* A LiveKit Cloud project
* LiveKit URL
* LiveKit API Key
* LiveKit API Secret
* A modern web browser
* Microphone

The project uses LiveKit Inference for the configured speech-to-text, LLM, and text-to-speech models. The inference API reads the LiveKit credentials from environment variables when they are not supplied directly in code.

---

# 📥 1. Install uv

This project uses **uv** for Python environment and dependency management.

Check whether uv is already installed:

```bash
uv --version
```

If the command works, continue to the next step.

If you do not have uv installed, install it from the official uv documentation:

https://docs.astral.sh/uv/

---

# 📥 2. Clone the Repository

Open **CMD** or **PowerShell**:

```bash
git clone https://github.com/shah-zaib-arsh/shah-zaib-arsh-livekit_agent.git
```

Move into the project directory:

```bash
cd shah-zaib-arsh-livekit_agent
```

---

# 📦 3. Install Project Dependencies

Run:

```bash
uv sync
```

This creates the project's virtual environment and installs the dependencies defined in `pyproject.toml`.

After installation, you should have a `.venv` folder.

---

# 🔐 4. Create the `.env` File

Create a file named:

```text
.env
```

in the project root.

Your project should look like this:

```text
shah-zaib-arsh-livekit_agent/
│
├── .env
├── README.md
├── agent.py
├── app.py
├── pyproject.toml
├── .python-version
└── src/
```

Add your LiveKit credentials:

```env
LIVEKIT_URL=wss://your-project.livekit.cloud
LIVEKIT_API_KEY=your_livekit_api_key
LIVEKIT_API_SECRET=your_livekit_api_secret
```

Replace the values with your actual LiveKit Cloud credentials.

For example:

```env
LIVEKIT_URL=wss://example-project.livekit.cloud
LIVEKIT_API_KEY=your_actual_key
LIVEKIT_API_SECRET=your_actual_secret
```

### Important

Never upload your `.env` file to GitHub.

Your `.env` file contains secret credentials.

---

# 🔒 5. Create `.gitignore`

Create a file named:

```text
.gitignore
```

Add:

```gitignore
.env
.venv/
__pycache__/
*.pyc
```

This prevents private credentials and local Python files from being committed to GitHub.

---

# ▶️ 6. Start the LiveKit Voice Agent

Open **Terminal 1** inside the project folder.

Run:

```bash
uv run agent.py dev
```

Your `agent.py` uses:

```python
agents.cli.run_app(server)
```

which provides the Python agent command interface used by commands such as `uv run agent.py dev`.

Keep this terminal running.

The agent needs to be running before you try to connect from the browser.

---

# 🌐 7. Start the Gradio Web App

Open **Terminal 2**.

Make sure you are inside the same project directory:

```bash
cd shah-zaib-arsh-livekit_agent
```

Run:

```bash
uv run app.py
```

Your Gradio application will start on:

```text
http://127.0.0.1:7860
```

Gradio's `Blocks` interface is served using the `launch()` method, which is what this project uses.

---

# 🌍 8. Open the Application

Open your browser and go to:

```text
http://127.0.0.1:7860
```

You should see:

```text
🎙️ LiveKit Voice AI Assistant

Connect your microphone and talk to your LiveKit AI voice agent.
```

---

# 🎤 9. Connect to the Voice Agent

Follow these steps:

### Step 1

Enter your name.

Example:

```text
Shahzaib
```

### Step 2

You can leave the **Room Name** empty.

The application will automatically generate a unique room.

Or enter your own room name:

```text
my-test-room
```

### Step 3

Click:

```text
Create Voice Session
```

### Step 4

Click:

```text
Connect
```

### Step 5

When the browser asks for microphone permission, click:

```text
Allow
```

### Step 6

Click:

```text
Enable Audio
```

### Step 7

Speak into your microphone.

The AI assistant should receive your voice, process it, and respond with audio.

---

# 🔄 How the Project Works

```text
                    USER
                      │
                      ▼
             ┌─────────────────┐
             │ Gradio Web App  │
             └────────┬────────┘
                      │
                      ▼
             Create LiveKit Token
                      │
                      ▼
             ┌─────────────────┐
             │  LiveKit Room   │
             └────────┬────────┘
                      │
             Microphone Audio
                      │
                      ▼
             ┌─────────────────┐
             │   AI Agent      │
             │    agent.py     │
             └────────┬────────┘
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
      STT            LLM           TTS
  AssemblyAI      Google Gemma   Fish Audio
        │             │             │
        └─────────────┼─────────────┘
                      │
                      ▼
              AI Voice Response
                      │
                      ▼
                 LiveKit
                      │
                      ▼
                  Browser
```

---

# 🧠 AI Voice Pipeline

The current `agent.py` uses:

```text
Microphone
    ↓
LiveKit
    ↓
AssemblyAI Universal 3.5 Pro
    ↓
Google Gemma 4 31B IT
    ↓
Fish Audio S2.1 Pro
    ↓
LiveKit
    ↓
User Speaker
```

The model configuration in `agent.py` is:

```python
stt=inference.STT(
    model="assemblyai/universal-3-5-pro",
    language="en"
)

llm=inference.LLM(
    model="google/gemma-4-31b-it"
)

tts=inference.TTS(
    model="fishaudio/s2.1-pro",
    voice="fa4c9eb3dccc4806b382b40d61c6b10a"
)
```

These model descriptors follow the LiveKit Inference model format.

---

# 🎙️ Microphone Features

The browser interface includes:

* Microphone permission
* Microphone publishing to LiveKit
* Live waveform visualization
* Microphone status
* Mute
* Unmute
* AI audio playback
* Disconnect
* Remote audio track handling

When you speak, the microphone waveform should respond to your voice.

---

# 🔊 Audio Controls

The application provides four main controls:

```text
Connect
Mute / Unmute
Enable Audio
Disconnect
```

### Connect

Connects your browser to the LiveKit room.

### Mute

Stops microphone audio from being published.

### Enable Audio

Enables browser playback for the AI assistant's voice.

### Disconnect

Leaves the LiveKit room and stops the current voice session.

---

# 🧪 Optional: Test the Agent Without the Gradio UI

You can also run the Python agent directly in console mode:

```bash
uv run agent.py console
```

This is useful for checking the agent independently from the browser UI.

For development mode:

```bash
uv run agent.py dev
```

The LiveKit CLI documentation also describes `lk agent dev` as the newer development command, while the Python `run_app()` interface used by this project is being phased out in favor of the LiveKit CLI.

For this repository, `uv run agent.py dev` matches the current project code and is the simplest command to use.

---

# 🐛 Troubleshooting

## `LIVEKIT_URL is missing`

Check your `.env` file:

```env
LIVEKIT_URL=wss://your-project.livekit.cloud
```

Make sure the `.env` file is in the same directory as `app.py`.

---

## `LIVEKIT_API_KEY or LIVEKIT_API_SECRET is missing`

Check that both values exist:

```env
LIVEKIT_API_KEY=your_key
LIVEKIT_API_SECRET=your_secret
```

---

## Agent does not connect

Make sure Terminal 1 is running:

```bash
uv run agent.py dev
```

Then run the Gradio application in Terminal 2:

```bash
uv run app.py
```

Both processes need to be running.

---

## Browser does not access the microphone

Check your browser's site permissions and allow microphone access for:

```text
http://127.0.0.1:7860
```

Then refresh the page and try connecting again.

---

## AI voice is not playing

After connecting, click:

```text
Enable Audio
```

Some browsers require a user interaction before audio playback is allowed.

---

## `uv` command not found

Install uv and restart CMD or PowerShell.

Then check:

```bash
uv --version
```

---

## Dependency errors

Run:

```bash
uv sync
```

again.

You can also verify the Python version:

```bash
python --version
```

The project is configured for:

```text
Python 3.14
```

---

# 🔒 Security

Never commit these files or secrets:

```text
.env
LIVEKIT_API_KEY
LIVEKIT_API_SECRET
```

Use environment variables instead.

Before pushing the repository:

```bash
git status
```

Make sure `.env` is not listed as a file to commit.

---

# 🚀 Quick Start

For a quick setup, the main commands are:

```bash
git clone https://github.com/shah-zaib-arsh/shah-zaib-arsh-livekit_agent.git

cd shah-zaib-arsh-livekit_agent

uv sync
```

Create `.env`:

```env
LIVEKIT_URL=wss://your-project.livekit.cloud
LIVEKIT_API_KEY=your_livekit_api_key
LIVEKIT_API_SECRET=your_livekit_api_secret
```

Then open two terminals.

### Terminal 1

```bash
uv run agent.py dev
```

### Terminal 2

```bash
uv run app.py
```

Open:

```text
http://127.0.0.1:7860
```

Then:

```text
Create Voice Session
        ↓
Connect
        ↓
Allow Microphone
        ↓
Enable Audio
        ↓
Start Talking
```

---

# 👨‍💻 Author

**Muhammad Shahzaib**

GitHub:
https://github.com/shah-zaib-arsh

LinkedIn:
https://www.linkedin.com/in/muhammad-shahzaib-arshed/

---

# 📌 Future Improvements

Possible future improvements:

* Conversation history
* Chat transcript display
* User authentication
* Multiple AI voices
* Multiple AI personalities
* Voice selection
* Persistent conversation storage
* Better mobile support
* Public deployment
* Additional AI models
* Advanced analytics and monitoring

---

# 📄 License

This project was created for learning, experimentation, and educational purposes.

---

⭐ If you find this project useful, consider giving the repository a star.
