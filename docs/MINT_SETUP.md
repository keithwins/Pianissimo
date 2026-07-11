# Mint laptop — one-time setup

Open this file on the Mint machine in a browser (no copy-paste from the other PC needed):

https://github.com/keithwins/Pianissimo/blob/main/docs/MINT_SETUP.md

(If these docs are not pushed yet, use the Syncthing drop folder or Matrix — see below.)

## 0. Crosstalk options (pick one)

You do **not** need a new Matrix server.

| Method | Good for | Notes |
|--------|----------|--------|
| **Syncthing** shared folder | Dropping scripts, sessions, library | Best ongoing LAN file sync; already planned |
| **Samba share** (shared “drive”) | Browse a folder from both PCs like a network drive | Fine; a bit more setup than Syncthing |
| **Matrix room** (existing server) | Paste a command or note | Instant; not for big video |
| **GitHub in browser** | Reading this doc / cloning after `gh` exists | Works when repo is pushed |
| **SSH** later | Remote terminal | Optional; not required tonight |

**Clipboard:** a network drive does **not** by itself sync copy-paste. For clipboard you’d want something like Input Leap / Barrier, or just paste into Matrix / a shared `inbox.txt`.

Recommended tonight: finish **Syncthing**, put an `inbox/` folder in the share, and/or use **Matrix** for short pastes.

## 1. Install GitHub CLI (`gh`)

Mint is a separate machine from Windows/WSL — install even if those already have `gh`.

```bash
(type -p wget >/dev/null || (sudo apt update && sudo apt-get install wget -y)) \
  && sudo mkdir -p -m 755 /etc/apt/keyrings \
  && out=$(mktemp) && wget -nv -O$out https://cli.github.com/packages/githubcli-archive-keyring.gpg \
  && cat $out | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
  && sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
  && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
  && sudo apt update \
  && sudo apt install gh -y
```

```bash
gh auth login
# GitHub.com → HTTPS → Login with browser → yes to Git credentials if asked
```

```bash
gh auth status
gh repo clone keithwins/Pianissimo
cd Pianissimo
```

Without `gh` yet:

```bash
sudo apt update && sudo apt install -y git
git clone https://github.com/keithwins/Pianissimo.git
```

## 2. Syncthing (LAN files)

```bash
sudo apt install -y syncthing
syncthing
```

Web UI: http://127.0.0.1:8384 — decline usage reporting if you want; add the desktop as a device; share:

- `~/Pianissimo-library`
- `~/Pianissimo-sessions`
- optional: `~/Pianissimo-inbox` for dropping `notes.txt` / scripts between machines

## 3. Quick MIDI check (when at the RD-88)

```bash
sudo apt install -y alsa-utils
aseqdump -l
# note the client number for the RD-88, then:
# aseqdump -p CLIENT:PORT
```

Play keys — events should print.
