# ParedraVoice

Local, privacy-preserving system-wide dictation for macOS. Hold Right Option, speak, release — cleaned text appears at your cursor. All processing on-device via MLX.

## Download

Grab the latest `.dmg` from the [Releases page](https://github.com/lhstorm/paredra_voice_releases/releases).

1. Open the DMG.
2. Drag `ParedraVoice.app` into `Applications`.
3. Launch it from `Applications`. The DMG is signed with an Apple Developer ID and notarized by Apple — Gatekeeper should launch it without warnings.

### First launch

You'll need to grant two permissions, once:

1. **Microphone** — macOS prompts automatically on first launch. Approve.
2. **Accessibility** — required for the global hotkey and text injection. Open **System Settings → Privacy & Security → Accessibility**, add `/Applications/ParedraVoice.app`, toggle it on.

The first launch also downloads ~5 GB of model weights from HuggingFace (one-time). The menu-bar icon shows progress while this is happening.

## Requirements

- macOS 14 (Sonoma) or later
- Apple Silicon (M1+)
- ~5 GB disk for model weights
- ~5 GB RAM while models are loaded (freed when idle)

## Features

- **Hold-to-talk dictation** — works in every app
- **On-device AI** — Parakeet-TDT 0.6B (STT) + Gemma 3 4B (cleanup). No network calls after setup.
- **Custom vocabulary** — plain text file of proper nouns and technical terms
- **Voice commands** — "delete that", "new paragraph", "new line"
- **Smart resource management** — models unload after 15 s idle, reload on next key-down
- **Password-field refusal** — won't type into secure text fields

## Verifying your download

```bash
spctl --assess --type open --context context:primary-signature --verbose \
  /Applications/ParedraVoice.app
# Expected: source=Notarized Developer ID
```

## Support

Bug reports and feature requests: [GitHub Issues](https://github.com/lhstorm/paredra_voice_releases/issues)
