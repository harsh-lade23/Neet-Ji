# 🧬 Neet Ji: AI-Powered Adaptive Assessment Engine

An intelligent Android application designed for JEE and NEET aspirants. Neet Ji moves beyond static question banks by utilizing a hybrid data architecture (RAG-lite) that combines local, deterministic database queries with dynamic, LLM-generated content via the Grok API. 

---

## 🎯 The Engineering Challenge
Static quiz applications eventually run out of questions, and standard AI chatbots are too unstructured for rigorous academic testing. 

**Neet Ji solves this by bridging classical app state with agentic AI.** It queries a local database first. If the local question bank is exhausted for a specific physics, chemistry, or math topic, the app dynamically constructs a context-aware prompt, interfaces with the Grok API, and generates strictly formatted, progressively difficult questions on the fly to fill the gap.

## 🚀 Core Features

*   **Hybrid RAG-Lite Data Pipeline:** Prioritizes verified local data (Room DB / JSON) for speed and accuracy, seamlessly falling back to generative AI only when necessary to ensure an infinite testing pool.
*   **Structured Output Engineering:** Utilizes strict system prompting to force the Grok API to return questions, options, and answers in a verifiable JSON format. This allows the application to predictably parse the data and render native UI components, rather than just displaying a wall of generated text.
*   **Progressive Difficulty Scaling:** The prompt engineering dynamically adjusts the context to ensure newly generated questions gradually increase in cognitive load, mimicking real exam patterns.
*   **Agentic Conversational Fallback:** During a test, users can request AI-generated hints or detailed explanations. If the structured explanation is insufficient, the app gracefully transitions the user into an open-ended conversational context (chat mode) to drill down into the core concepts.

---

## 🏗️ System Architecture & Data Flow

1.  **Topic Selection:** User selects a subject and topic (e.g., *Rotational Motion*).
2.  **Local Query:** The app queries the local `Room` database for existing questions.
3.  **Logic Gate:** If `local_questions.size < requested_quiz_length`, the app calculates the deficit.
4.  **API Inference:** The app sends a highly constrained prompt to the Grok API requesting exactly `N` questions of increasing difficulty, formatted strictly as a JSON array.
5.  **State Merging:** The app deserializes the API response, merges it with the local deterministic questions, and feeds the unified list to the Jetpack Compose UI state layer.
6.  **Interactive Evaluation:** The app tracks user performance and manages the state of the "Hint / Explain / Chat" agentic lifecycle.

---

## 🛠️ Tech Stack

*   **Language:** Kotlin
*   **UI Toolkit:** Jetpack Compose (Declarative UI)
*   **Local Persistence:** Room Database, JSON parsing
*   **Network/API:** Retrofit / OkHttp
*   **AI Engine:** Grok API
*   **Architecture:** MVVM (Model-View-ViewModel) with Kotlin Coroutines for asynchronous network and database operations

---

## 📱 Screenshots 

*(Placeholder: Add 2-3 screenshots here showing the Quiz UI, the structured Explanation UI, and the Chat Fallback UI)*

---

## 💡 Future Enhancements
*   Implement local caching of high-quality AI-generated questions back into the Room database to reduce future API calls.
*   Add user-specific performance tracking to fine-tune the difficulty scaling in the API prompt based on historical accuracy.

---
*Developed as a showcase of structured, agentic mobile software engineering.*
