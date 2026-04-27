# Aditya LLM App 🤖

**A minimal Android app that runs LLM locally on device — no internet needed.**

---

## 📱 About

This app demonstrates on-device AI inference using the RunAnywhere Kotlin SDK and llama.cpp. The LLM runs fully locally on the Android device — no cloud, no internet, no data leaves the device.

Built as part of a take-home task for MetaMenu to demonstrate end-to-end mobile AI development.

---

## 🎥 Demo


| <img width="250" height="532" alt="Screenshot 2026-04-27 110327" src="https://github.com/user-attachments/assets/55e37ad2-5c92-48cf-9c5e-c5f223da9f38" />
| <img width="238" height="511" alt="Screenshot 2026-04-27 110303" src="https://github.com/user-attachments/assets/f9165dcb-26a2-4b06-9fcf-b4c6f3530fb4" />
| <img width="294" height="555" alt="image" src="https://github.com/user-attachments/assets/8941a33c-f1cf-4ed1-b0c2-a3f5871cb42b" />
| <img width="251" height="535" alt="Screenshot 2026-04-27 110244" src="https://github.com/user-attachments/assets/0d5930c9-7f11-4bda-9a43-bd3abd868bf9" />


---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Platform | Android (Kotlin) |
| LLM Runtime | llama.cpp |
| SDK | RunAnywhere Kotlin SDK |
| Model | SmolLM2 360M (GGUF format) |
| Inference | 100% on-device, fully offline |
| Min SDK | API 24 (Android 7.0) |

---

## 🚀 How It Works

1. App initializes the RunAnywhere Kotlin SDK
2. Downloads and loads a GGUF model (SmolLM2 360M ~400MB)
3. User types a message
4. LLM generates a response locally on device
5. No internet connection required at inference time

```kotlin
// Initialize
LlamaCPP.register()
RunAnywhere.initialize(environment = SDKEnvironment.DEVELOPMENT)

// Load model
RunAnywhere.downloadModel("smollm2-360m").collect { println("${it.progress * 100}%") }
RunAnywhere.loadLLMModel("smollm2-360m")

// Generate response
val response = RunAnywhere.chat(userInput)
```

---

## 📦 Setup & Installation

### Prerequisites
- Android Studio
- JDK 17+
- Android SDK API 24+

### Steps
```bash
# Clone the repo
git clone https://github.com/adityakr09/Aditya-LLM-App.git

# Open in Android Studio
File → Open → Select the project folder

# Run on device or emulator
Click ▶️ Run button
```

---

## 📁 Project Structure

```
Aditya-LLM-App/
├── examples/
│   └── android/
│       └── RunAnywhereAI/      # Main Android app
│           ├── app/
│           │   └── src/main/
│           │       ├── kotlin/ # Kotlin source code
│           │       └── res/    # Resources
│           └── build.gradle.kts
├── sdk/
│   └── runanywhere-kotlin/     # RunAnywhere Kotlin SDK
└── README.md
```

---

## ⚙️ Key Dependencies

```kotlin
dependencies {
    implementation("com.runanywhere.sdk:runanywhere-kotlin:0.16.1")
    implementation("com.runanywhere.sdk:runanywhere-core-llamacpp:0.16.1")
}
```

---

## 🤖 Supported Models

| Model | Size | RAM Required |
|---|---|---|
| SmolLM2 360M | ~400MB | 500MB |
| Qwen 2.5 0.5B | ~500MB | 600MB |
| Llama 3.2 1B | ~1GB | 1.2GB |

---

## ⚠️ Known Limitations

- App may crash on x86 emulator due to ARM native library alignment (known issue with llama.cpp on x86)
- Requires 2GB+ RAM for smooth inference
- First model download requires internet (~400MB)

---

## 👨‍💻 Built By

**Aditya Kumar**  
Backend & Full-Stack Developer  
Django • REST APIs • React • Android (learning)

---

## 📄 License

Apache 2.0
