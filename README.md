# ZEN32 Countdown Timer Switch

A Home Assistant blueprint that turns a [Zooz ZEN32](https://www.getzooz.com/zooz-zen32-scene-controller/)
Z-Wave scene controller into a countdown timer switch, using the 4 small
buttons as preset timespans and their LEDs as a remaining-time gauge, and
the big paddle as always-available manual on/off.

## Import into Home Assistant

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fgtporter-personal%2Fzen32-countdown-timer-switch%2Fblob%2Fmain%2Fzen32_countdown_timer_switch.yaml)

Or manually: Settings > Automations & Scenes > Blueprints > Import Blueprint,
and paste this URL:

```
https://github.com/gtporter-personal/zen32-countdown-timer-switch/blob/main/zen32_countdown_timer_switch.yaml
```

## Requirements

- A Zooz ZEN32 scene controller paired via the Z-Wave JS integration.
- A `timer` helper (Settings > Devices & Services > Helpers > Create Helper > Timer).
  Duration doesn't matter, it's overridden on every button press.
- An `input_select` (dropdown) helper with exactly these five options:
  `Off`, `On - Countdown Timer`, `On - Humidity Control`,
  `On - External Automation`, `On - Manual`.
- Optional: a Generic Hygrostat helper (domain `humidifier`, Dehumidifier
  mode) controlling the same switch, if you want automatic humidity control
  reflected on the paddle LED and dropdown.

## What it does

- **Big paddle**: manual on/off, always available. Its LED shows *why* the
  switch is on - solid for manual, blinking for this blueprint's countdown,
  blinking a different color when the optional hygrostat is actively
  dehumidifying, blinking a fourth color for any other automation.
- **Small buttons 1-4**: press one while the switch is off to turn it on for
  that button's configured time. Press one while it's already on to
  restart the countdown at the new duration.
- **LEDs 1-4**: show remaining time like a fuel gauge - solid for time
  already banked, blinking for the current bracket, off for brackets not
  yet reached.

Full behavior notes and setup details are in the blueprint's own
description, visible after import.

## License

MIT
