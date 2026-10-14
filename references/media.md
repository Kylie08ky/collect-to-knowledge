# Media inputs and optional transcription

This skill organizes knowledge; it does not include a downloader or speech model.
Use supplied transcripts or accessible official captions first.

## Optional local transcription

Recommended companion: [hotcatty/media-transcriber](https://github.com/hotcatty/media-transcriber).
Install separately, read its current SKILL.md, and follow its supported CLI.
The upstream project lists Xiaoyuzhou, Bilibili, Xiaohongshu video, YouTube,
Apple Podcasts, and local audio/video. Platform support is conditional on link
access, authentication, downloader support, and upstream changes.

A Xiaoyuzhou episode and a Xiaohongshu video were successfully transcribed during
development on Windows with faster-whisper and an NVIDIA GPU. This is a bounded
test, not a guarantee for all links, hardware, or other hosts.

Dependencies such as Python, FFmpeg, Whisper model files, and GPU libraries
belong to the transcriber and are not bundled. First-run model downloads can be
large; CPU/GPU speed varies. The local ASR route needs no DashScope key.
The AI host, image generation, or optional cloud services may have their own costs.

### Installation prompt users can give their AI

“Install the local skill from https://github.com/hotcatty/media-transcriber.
Read its current installation instructions, detect my operating system and
available Python/FFmpeg/hardware, prepare an isolated environment, and test one
source. Keep transcription local. Do not copy another computer's paths.”

On macOS/Linux, the upstream CLI currently uses:
```bash
bash /path/to/media-transcriber/scripts/run.sh "SOURCE" --out "/path/to/work/transcript"
```

On Windows, check the upstream instructions for native support. A Bash wrapper
that uses `.venv/bin/python` cannot simply be run as a PowerShell command.
When an isolated environment and FFmpeg are prepared, the installed upstream
Python entry point can be invoked with Windows paths:
```powershell
& '<media-transcriber>/.venv/Scripts/python.exe' -X utf8 '<media-transcriber>/scripts/transcribe.py' 'SOURCE' --out '<work-directory>'
```
The paths above are placeholders, not executable defaults. Configure FFmpeg on
PATH and any supported model/cache/GPU settings for that machine. Inspect the
installed entry point before using this command after upstream changes. Do not
invent a per-user CUDA path or assume an NVIDIA GPU exists.

Optional Xiaoyuzhou helper:
[weisi-gu/xiaoyuzhou-podcast-notes](https://github.com/weisi-gu/xiaoyuzhou-podcast-notes).
It can retrieve metadata/available official transcription; its cloud ASR routes
require separate configuration and user authorization. Do not silently send
audio to a cloud provider or retry paid jobs across backends.

## Source boundaries

- Image/text posts need text/image reading; speech recognition does not perform OCR.
- For inaccessible, removed, paywalled, or login-only sources, state the actual
  limitation and request a usable excerpt/file when appropriate.
- Never export browser cookies or upload source audio without explicit authorization.
- Keep original media and intermediate ASR in a task work directory, outside git.
- Read the full transcript; compare first/last speech and duration, look for large
  gaps, repetition, and questionable formulas/names. Audio transcription cannot
  prove coverage of visual-only content.
- Label automated output as unverified word for word. Do not silently repair
  uncertain wording into invented quotations.
- For third-party copyrighted links, use transcripts internally for analysis and
  deliver original synthesis with brief quotations, not a full verbatim export.
  User-supplied/owned or otherwise permitted material may be handled differently
  under the host's rules.

“Local transcription” describes ASR, not the entire workflow: the assistant host
processes content under its own data handling, and authorized summaries/images
are sent to Notion. Do not advertise this workflow as fully offline or end-to-end
local.
