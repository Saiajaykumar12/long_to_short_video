## Result

This pipeline fully eliminated manual video editing from the content workflow at Ecowoodies. A long-form video that previously required ~2 hours of manual editing now produces a highlight clip automatically in under 5 minutes — transcription, clip selection, and rendering handled end-to-end by the pipeline.

# Long Video to Short Clips — AI Automation (n8n)

Paste a video URL into Google Sheets → get a short highlight clip back in the same row.
No manual editing. No timeline scrubbing. Fully automated.

## The Problem It Solves

Content creators spend hours manually clipping long videos into short-form content.
This workflow does it end-to-end using AI — transcription, moment detection, rendering —
triggered by a single spreadsheet entry.

## Pipeline Architecture
Google Sheets (video URL added)
↓
AssemblyAI — full video transcription with timestamps
↓
Groq LLaMA 3.3 70B — identifies 3–5 best moments from transcript
↓
Shotstack — renders highlight clip from selected timestamps
↓
Cloudinary — hosts the final video
↓
Google Sheets — output link written back to same row

## Tools Used

| Tool | Role |
|------|------|
| n8n | Workflow orchestration |
| Google Sheets | Trigger + output destination |
| AssemblyAI | Video transcription with sentence-level timestamps |
| Groq LLaMA 3.3 70B | AI moment detection from transcript |
| Shotstack | Programmatic video rendering |
| Cloudinary | Video hosting and delivery |

## How to Use

1. Import `Sheets long to short video (2).json` into your n8n instance
2. Set up credentials: AssemblyAI, Groq, Shotstack, Cloudinary, Google Sheets
3. Replace the Google Sheet ID in the trigger node with your own
4. Add columns `video_url` and `row_number` to your sheet
5. Activate the workflow and paste any public video URL into the sheet
6. Output clip link appears in the same row within minutes

## Key Design Decisions

- **Sentence-level timestamps from AssemblyAI** — word-level would be noisier;
  sentence-level gives cleaner clip boundaries
- **LLaMA 3.3 70B over smaller models** — smaller models picked generic moments;
  70B understood context and narrative arc better
- **Cloudinary over direct Shotstack storage** — easier to share and embed output links

## Environment / Credentials Required

- AssemblyAI API key
- Groq API key
- Shotstack API key
- Cloudinary account (cloud name, API key, secret)
- Google Sheets OAuth2 connection in n8n
