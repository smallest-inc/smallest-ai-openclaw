# ⚡ Smallest AI — OpenClaw Voice Skill

The fastest TTS/STT skill for [OpenClaw](https://openclaw.ai). Sub-100ms text-to-speech via Lightning. 64ms speech-to-text via Pulse.

> **"My OpenClaw now speaks faster than I can think"** — what you'll say after installing this

## Why This Exists

| Provider | Latency (TTFB) | Price | Voice Cloning |
|----------|---------------|-------|---------------|
| **Smallest AI** | **~100ms** | **Free tier + $5/mo** | **5 sec of audio** |
| ElevenLabs | ~300ms | $5/mo (30min) | 30 sec of audio |
| OpenAI TTS | ~200ms | Pay per token | Not available |
| Kokoro (Local) | Varies | Free (GPU needed) | Not available |

Smallest AI is faster, cheaper, and needs 6x less audio for voice cloning.

## Quick Install

```bash
# Option 1: ClawHub (recommended)
clawhub install smallest-ai

# Option 2: Manual
git clone https://github.com/smallest-inc/smallest-ai-openclaw.git
cp -r smallest-ai-openclaw ~/.openclaw/workspace/skills/smallest-ai

# Set your API key
export SMALLEST_API_KEY="your_key_here"
# Get one free at https://waves.smallest.ai
```

Then ask your OpenClaw agent to **"refresh skills"** or restart the gateway.

## What You Get

### 🗣️ Text-to-Speech (Lightning)
```
"Hey Claw, say good morning in Arman's voice"
"Read my latest email summary aloud"
"Generate a voice note saying the meeting is at 3pm"
```

### 🎙️ Speech-to-Text (Pulse)
```
"Transcribe this voice note" [attach audio]
"What did they say in this recording? Include speaker labels"
"Convert this meeting audio to text with timestamps"
```

### 🌍 Multilingual
```
"Say 'नमस्ते, कैसे हैं आप?' in Hindi"
"Read this in French: Bonjour le monde"
```

## Voices

| Voice | Style | Best For |
|-------|-------|----------|
| `emily` | Female, neutral | General use (default) |
| `jasmine` | Female, warm | Storytelling, greetings |
| `arman` | Male, professional | Reports, briefings |
| `arnav` | Male, conversational | Casual updates |
| `mithali` | Female, Hindi-native | Hindi, code-switching |

## Configuration

Add to your `openclaw.json` to set as default TTS:

```json
{
  "skills": {
    "entries": {
      "smallest-ai": {
        "apiKey": "your_smallest_api_key"
      }
    }
  }
}
```

### Use with Cron/Heartbeat

Add to your `HEARTBEAT.md`:
```markdown
- Every morning at 8am, summarize today's calendar and read it aloud using smallest-ai TTS
- When a high-priority Slack message arrives, generate a voice alert
```

## File Structure

```
smallest-ai/
├── SKILL.md                 # Skill definition (required)
├── scripts/
│   ├── tts.sh               # TTS via curl (zero deps)
│   ├── tts.py               # TTS via Python (SDK + fallback)
│   ├── stt.sh               # STT via curl
│   ├── stt.py               # STT via Python
│   └── voices.sh            # List available voices
├── references/
│   ├── voices.md            # Voice catalog
│   ├── languages.md         # 30+ supported languages
│   └── api-reference.md     # API quick reference
└── README.md                # This file
```

## Requirements

- OpenClaw (any version)
- `curl` (included on macOS/Linux)
- `python3` (optional, for advanced features)
- `SMALLEST_API_KEY` environment variable

Optional: `pip install smallestai` for the official SDK with async support and streaming.

## Examples

### Morning Briefing Agent
```
"Every morning at 7am, check my calendar and email,
 summarize the day ahead, and read it to me on WhatsApp
 using the arman voice"
```

### Meeting Transcription
```
"Transcribe this meeting recording, identify who said what,
 and create a summary with action items"
```

### Multilingual Newsletter
```
"Take my latest blog post and create audio versions
 in English, Hindi, and Spanish"
```

## Pricing

| Plan | TTS | STT | Voice Clones | Cost |
|------|-----|-----|-------------|------|
| Free | 30 min/mo | Limited | 0 | $0 |
| Basic | 3 hrs/mo | Included | 1 | $5/mo |
| Premium | 24 hrs/mo | Included | 2 | $29/mo |

## Links

- [Smallest AI](https://smallest.ai) — Main site
- [Waves Console](https://waves.smallest.ai) — Get API key
- [API Docs](https://waves-docs.smallest.ai) — Full documentation
- [Python SDK](https://github.com/smallest-inc/smallest-python-sdk) — Official SDK
- [OpenClaw](https://openclaw.ai) — OpenClaw main site
- [ClawHub](https://clawhub.com) — Skills marketplace

## Contributing

PRs welcome! If you add a new feature or voice integration, please include:
1. Updated SKILL.md instructions
2. Tests or usage examples
3. Updated references if API surface changes

## License

MIT — use it, fork it, ship it.

---

Built with ⚡ by [Abhishek](https://twitter.com/stalwartcoder) at [Smallest AI](https://smallest.ai)
