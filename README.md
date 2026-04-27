# Aditya LLM App 🤖

**A minimal Android app that runs LLM locally on device — no internet needed.**

---

## 📱 About

This app demonstrates on-device AI inference using the RunAnywhere Kotlin SDK and llama.cpp. The LLM runs fully locally on the Android device — no cloud, no internet, no data leaves the device.

Built as part of a take-home task for MetaMenu to demonstrate end-to-end mobile AI development.

---


## 📸 Screenshots

| App Launch | Checking Info | App Info |
|---|---|---|
| <img src="https://github.com/user-attachments/assets/d4697d11-ac3b-42a9-85d3-d5a9eee528e2" width="200"/> | <img src="https://github.com/user-attachments/assets/1db95d5a-fbcf-437b-a253-bc5a89703a74" width="200"/> | <img src="https://github.com/user-attachments/assets/2785bf62-8284-425a-8564-f9f00ca4e480" width="200"/> |

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
