# vid2kg annotation tool

A single page tool for logging ground-truth recipe data from cooking videos: ingredients, quantities, and steps, used to evaluate the [vid2kg](https://github.com/samyak-io/vid2kg-final) extraction pipeline.

Live: https://samyak-io.github.io/annotation-tool-vid2kg/

## What it does

Paste a YouTube URL, watch the video, and log:
- ingredients (name, quantity, unit, and where the info came from: spoken / visual / inferred)
- steps (instruction, start/end timestamp)

Download as JSON when done. Load a saved JSON to keep editing later.

## Output format

```json
{
  "video_url": "...",
  "video_id": "...",
  "title": "Upma",
  "language": "Malayalam",
  "ingredients": [
    {"name": "semolina", "quantity": "1", "unit": "cup", "source": "spoken"}
  ],
  "steps": [
    {"instruction": "Roast the semolina until fragrant", "start": "0:12", "end": "0:45"}
  ]
}
```

`source` is `spoken`, `visual`, or `inferred`.

## Limitations

- Annotator needs to understand the spoken language to log `spoken` entries accurately.
- Timestamps are read off the player manually, not captured automatically.
- One file, no build step, nothing saved automatically, so download before closing the tab.

## Running locally

```bash
python3 -m http.server 8000
```
Open `http://localhost:8000/index.html`. Opening the file directly (`file://`) breaks the YouTube embed.

