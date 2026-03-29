# Operations

Japanese: [operations.ja.md](operations.ja.md)

## Day-to-Day Operation

### Apply updates on the Raspberry Pi side

```sh
cd ~/m5papers3
git pull
systemctl --user restart m5news-http.service
systemctl --user restart m5news-generate.timer
```

### Apply updates on the M5 side

```sh
cd /Users/tomato/Documents/Arduino/M5PaperS3_NewsDashboard
arduino-cli compile -b m5stack:esp32:m5stack_papers3 .
```

Then flash the built firmware to the device.

## Troubleshooting Flow

### When the M5 device cannot change pages

Check first:

- whether the Raspberry Pi HTTP server is running
- whether `index.png` is reachable
- whether `index.version` is reachable

### Raspberry Pi HTTP checks

```sh
systemctl --user status m5news-http.service
ss -tulpn | grep 8010
curl -I http://127.0.0.1:8010/index.png
```

### PNG generation checks

```sh
systemctl --user status m5news-generate.timer
journalctl --user -u m5news-generate.service -n 100 --no-pager
```

## Documentation Rules

- keep `README` as the entry point
- put detailed specifications under `docs/`
- prioritize design reasons and constraints over line-by-line code explanations
- when implementation changes, update only the related docs
