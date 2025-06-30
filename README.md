# 🔧 SETA – Smart Electronics Troubleshooting Assistant

SETA (Smart Electronics Troubleshooting Assistant) is an AI-powered assistant that helps users diagnose and fix problems with their electronic devices — using natural language, speech, and images.

> 🧠 Powered by Qwen2.5 VL 72B (via OpenRouter), Whisper, Roboflow, and FastAPI  
> 🗣️ Voice in, voice out. Chat with SETA like a human technician.  
> 📷 Upload photos of the issue for visual diagnosis.  
> 🎥 Get instant YouTube explainer links tailored to your problem.

---

## 🌟 Features

- 🤖 **AI Chatbot (LLM via OpenRouter)**
- 🗣️ **Voice Input + Output (Whisper + TTS)**
- 📷 **Screenshot / Image Upload for Visual Troubleshooting (YOLOv8 + Roboflow)**
- 🎥 **Auto YouTube Explainer Videos for Each Issue**
- 🛠️ **750+ Problem Knowledgebase for Phones + Laptops**
- 🌐 **FastAPI Backend + Vite/React Frontend**
- 💬 Multilingual, accessible, and user-friendly

---

## 🧱 Tech Stack

| Layer       | Technology |
|-------------|------------|
| LLM         | Qwen2.5 VL 72B (OpenRouter) |
| Vision      | Roboflow + YOLOv8 |
| Audio       | Whisper (Speech-to-Text) + Coqui TTS |
| Backend     | FastAPI |
| Frontend    | React + Vite + Tailwind |
| Storage     | Supabase |
| Deployment  | Bolt.new (live prototype)

---

## 🚀 How It Works

1. User opens SETA and chooses:
   - Text, Voice, or Image input
2. Message is sent to `/chat` endpoint (backend):
   - Powered by Qwen2.5 VL 72B
3. Response includes:
   - Troubleshooting steps
   - Optional YouTube explainer link
   - TTS voice reply
4. UI shows full history, model name, and speed

---

## 🧪 Demo

👉 Live preview: [https://bolt.new/~/sb1-gf4ucvxk](https://bolt.new/~/sb1-gf4ucvxk)  
📄 Full problem database: `SETA_750_Problems_Real_Names.txt`

---

## 🛠 API Endpoints

| Endpoint         | Purpose                         |
|------------------|----------------------------------|
| `/chat`          | Get AI response from LLM        |
| `/upload`        | Accept image for visual analysis|
| `/analyze`       | YOLOv8-based issue detection    |
| `/speech-to-text`| Converts voice to text (Whisper)|
| `/text-to-speech`| Speaks out the AI reply         |
| `/status`        | Health check                    |

---

## 📁 Folder Structure

```bash
├── backend
│   ├── main.py
│   ├── routes/
│   └── models/
├── frontend
│   ├── src/
│   │   └── components/chat/FullFeaturedChatInterface.jsx
│   └── .env
├── data/
│   └── SETA_750_Problems_Real_Names.txt
└── README.md# SETA
