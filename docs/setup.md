# Setup

Japanese: [setup.ja.md](setup.ja.md)

## Recommended Setup Order

To keep the installation process straightforward, use this order:

1. Set up the Raspberry Pi side first.
2. Confirm that `index.png` and `index.version` are available over HTTP.
3. Configure Wi-Fi and the server URL on the M5PaperS3 side.
4. Confirm page rendering and navigation on the device.
5. Confirm periodic refresh, priority prefetch, and `NEW / READ` behavior.

## 1. Raspberry Pi Side

Minimum tasks:

- create a Python virtual environment
- install `pillow` and `feedparser`
- place required fonts under `fonts/`
- confirm that `make_pages_png.py` can generate images
- confirm that `http.server` can serve `index.png`
- deploy the `systemd/` units into `~/.config/systemd/user/`

## 2. M5PaperS3 Side

Minimum tasks:

- write Wi-Fi settings into `config.h`
- build with Arduino IDE or `arduino-cli`
- flash the firmware to the M5PaperS3
- confirm that the `index` page appears
- confirm page navigation by tap and swipe

## 3. Integration Check

Check on the Raspberry Pi side:

- `curl -I http://127.0.0.1:8010/index.png`
- `systemctl --user status m5news-http.service`
- `systemctl --user status m5news-generate.timer`

Check on the M5 side:

- `index` display
- detail page transitions
- periodic refresh
- top-right `NEW / READ` indication

## Update Workflow

### When Raspberry Pi code changes

1. Edit `m5papers3-news-server` on the Mac
2. commit / push
3. run `git pull` on the Raspberry Pi
4. restart services or timers if needed

### When M5 device code changes

1. Edit `M5PaperS3_NewsDashboard` on the Mac
2. commit / push
3. rebuild and flash the M5PaperS3
