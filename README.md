# sf-iot-firmware

Published firmware for the dental lab mill monitors. Served by GitHub Pages at
the domain in `CNAME`.

**Public on purpose.** The binary contains no secrets — WiFi credentials are
never compiled in; each stick is provisioned at install via Improv. If a build
ever does contain them, `publish.sh` in the source repo refuses to stage it.

Owned by the `smileforge` org so public DNS names the business rather than an
individual. Source lives in a private repo. Nothing here is edited by hand: run
`./publish.sh <version>` there, which stages `dist/` and copies it here.

| File | |
|---|---|
| `manifest.json` | what sticks poll; names the version and the binary's md5 |
| `firmware.ota.bin` | the firmware itself |

Sticks poll every 6 hours. Upload the binary first and the manifest second — the
manifest is what announces a new version, so publishing it while the binary is
missing makes every stick that polls in between fail and retry.
