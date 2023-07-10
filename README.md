<div align="center">
<h1>Apx 2.0 Shell Script Installer</h1>
<p>The Automated Script Installer made by the Vanilla OS Team</p>
<sup>The Script was found in <a href="https://vanillaos.org/2023/07/05/vanilla-os-orchid-devlog.html">Vanilla OS Orchid - Devlog 5 Jul</a></sup>
</div>

## Run
Make sure you have `git` and `curl` installed 
```bash
git clone https://github.com/GabsEdits/apx-2.0-installer
```
```bash
cd apx-2.0-installer
```
```bash
sudo sh install.sh
```

## The Installer
```bash
#!/bin/bash

WORK_DIR="YOUR_WORK_DIR"  # <- edit this path

mkdir -p "$WORK_DIR"
cd "$WORK_DIR"

curl -LO https://github.com/89luca89/distrobox/archive/refs/tags/1.5.0.2.tar.gz
tar -xzf 1.5.0.2.tar.gz

curl -LO https://github.com/Vanilla-OS/apx/releases/download/continuous/apx.tar.gz
tar -xzf apx.tar.gz
mv apx "$HOME/.local/bin/apx2"
chmod +x "$HOME/.local/bin/apx2"

mkdir -p "$HOME/.config/apx"
echo '{
  "apxPath": "'"$HOME/.local/share/apx/"'",
  "distroboxpath": "'"$WORK_DIR/distrobox-1.5.0.2/distrobox"'",
  "storageDriver": "btrfs"
}' > "$HOME/.config/apx/apx.json"

git clone https://github.com/Vanilla-OS/vanilla-apx-configs.git "$WORK_DIR/vanilla-apx-configs"
mv "$WORK_DIR/vanilla-apx-configs/stacks" "$HOME/.local/share/apx/"
mv "$WORK_DIR/vanilla-apx-configs/package-managers" "$HOME/.local/share/apx/"

echo "Installation completed. You can now use Apx v2 by running 'apx2'."
apx2 --version
```
