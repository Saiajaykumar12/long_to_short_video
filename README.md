## Result

This pipeline fully eliminated manual video editing from the content workflow at Ecowoodies. A long-form video that previously required ~2 hours of manual editing now produces a highlight clip automatically in under 5 minutes — transcription, clip selection, and rendering handled end-to-end by the pipeline.

Input: long video URL
Output: short highlight clip, ready to post — zero human steps in between.

---

# 🎬 Sheets Long to Short Video Automation (n8n)
An automated n8n workflow that converts long videos into short highlight clips using AI — triggered directly from Google Sheets with zero manual effort.

## ⚙️ What It Does
- Triggers instantly when a new video URL is added to Google Sheets
- Transcribes the full video using AssemblyAI
- Identifies the 3–5 best moments using Groq LLaMA AI
- Renders a short highlight clip automatically via Shotstack
- Uploads the final video to Cloudinary
- Writes the output link back to your Google Sheet

## 🛠️ Tools Used
- n8n (workflow automation)
- Google Sheets (trigger + output)
- AssemblyAI (transcription)
- Groq LLaMA 3.3 70B (AI moment detection)
- Shotstack (video rendering)
- Cloudinary (video hosting)

## 🚀 How to Use
1. Import `Sheets_long_to_short_video__2_.json` into your n8n instance
2. Set up credentials for AssemblyAI, Groq, Shotstack, Cloudinary and Google Sheets
3. Replace the Google Sheet ID in the trigger node with your own
4. Add columns `video_url` and `row_number` to your sheet
5. Activate the workflow and paste a video URL into the sheet

## 📌 Key Features
- ✅ Fully automated — no manual editing required
- ✅ AI-powered clip selection using llama-3.1-8b-instant
- ✅ Sentence-level timestamp accuracy
- ✅ Outputs result link directly back to Google Sheets
- ✅ Works for any publicly accessible video URL
