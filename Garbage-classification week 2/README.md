# Waste Classifier Sustainability App – 60% Milestone

This repository contains a **Streamlit** web application that classifies waste images (paper, glass, metal … etc.) using a pretrained Keras model and then generates:

* The most relevant UN Sustainable Development Goals (SDGs) for the detected material.
* A short *awareness note* with an approximate carbon‑footprint figure powered by the OpenAI API.

> **Project status:** 60% complete  
> _Target: functional demo ready for internal review & viva._

---

## 1 . Quick start (local)

```bash
# 1. Create and activate a virtual environment (recommended)
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# 2. Install dependencies
pip install -r requirements.txt

# 3. Configure your OpenAI key
echo "OPENAI_API_KEY=sk‑..." > .env

# 4. Run the Streamlit app
streamlit run app.py
```

The browser should open automatically at **http://localhost:8501**.  
Upload a photo of waste to see the classification and SDG cards.

---

## 2 . Project structure

```
Waste-Classifier-Sustainability-App/
├── app.py              ← Streamlit UI + inference + OpenAI logic
├── keras_model.h5      ← MobileNetV3‑Large model (224 × 224, 4 classes)
├── labels.txt          ← Class index → human‑readable labels
├── sdg goals/          ← PNG/JPG assets for SDG tiles
├── requirements.txt
└── README.md           ← **You are here**
```

---

## 3 . Milestone deliverables

✅ Model loads once & is cached (no runtime lag).  
✅ Streamlit wide‑layout with three columns (preview • SDG cards • carbon note).  
✅ Error handling for:
* missing OpenAI key
* non‑image files
* model inference failures

✅ Clean, pinned dependency list (`requirements.txt`)  
✅ Cross‑platform run instructions (Windows / macOS / Linux)  
✅ Added **How‑to‑run video** link placeholder (to be recorded).  
⬜ Deploy to **Streamlit Community Cloud**  
⬜ SQLite activity log for uploaded predictions  
⬜ User authentication & dashboard (TBD)  
⬜ Unit tests + GitHub Actions CI (TBD)

---

## 4 . Common errors & fixes

| Symptom | Cause | Fix |
|---------|-------|-----|
| `ModuleNotFoundError: PIL` | Wrong package name | `pip install pillow` |
| `RuntimeError: Unable to open object (bad file signature)` | Corrupt `keras_model.h5` | Download fresh model | 
| Blank page after upload | Wrong image channel order | Ensure RGB mode (`.convert("RGB")`) |

---

## 5 . License

MIT (see `LICENSE`)
