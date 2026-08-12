<div align="center">

  <img src="https://raw.githubusercontent.com/stlity/Xilla/master/assets/xilla.png" alt="Xilla mountain logo" width="180">
  <h1>Xilla</h1>
  <p><strong>A modular Telegram userbot with a calm, mountain-inspired command center.</strong></p>
  <p>Self-hosted · Extensible · Built for deliberate control</p>

  <p>
    <a href="#">
      <img src="https://img.shields.io/github/languages/code-size/stlity/Xilla" alt="Code Size">
    </a>
    <a href="#">
      <img src="https://img.shields.io/github/issues-raw/stlity/Xilla" alt="Open Issues">
    </a>
    <a href="#">
      <img src="https://img.shields.io/github/license/stlity/Xilla" alt="License">
    </a>
    <a href="#">
      <img src="https://img.shields.io/github/commit-activity/m/stlity/Xilla" alt="Commit Activity">
    </a>
    <br>
    <a href="#">
      <img src="https://img.shields.io/github/forks/stlity/Xilla?style=flat" alt="Forks">
    </a>
    <a href="#">
      <img src="https://img.shields.io/github/stars/stlity/Xilla" alt="Stars">
    </a>
    <a href="https://github.com/psf/black">
      <img src="https://img.shields.io/badge/code%20style-black-000000.svg" alt="Code Style: Black">
    </a>
    <br>
    <a href="https://github.com/stlity/Xilla/blob/master/README.md">
      <img src="https://img.shields.io/badge/lang-en-red.svg" alt="En">
    </a>
    <a href="https://github.com/stlity/Xilla/blob/master/README_RU.md">
      <img src="https://img.shields.io/badge/lang-ru-green.svg" alt="Ru">
    </a>
  </p>
  
</div>

> **Xilla** is a self-hosted Telegram userbot that combines modular automation with a focused control surface. The project is designed for users who prefer to run their own instance, keep their configuration close, and extend functionality deliberately.

| Start here | What you will find |
|---|---|
| **New installation** | Setup commands for VPS, WSL and UserLAnd |
| **Existing Heroku installation** | A documented migration path that preserves data and sessions |
| **Daily use** | The `.help` command for discoverability and `.cfg` for interactive configuration |

## Security first

> **Treat third-party modules as executable code.** Install modules only from authors and repositories you trust, review unfamiliar commands before running them, and keep your session files private. Commands such as `.terminal`, `.eval` and `.ecpp` can affect the host system and should be used with particular care.

## Installation

### VPS / VDS

> **Running as root:** add `--root` to the start command to avoid the interactive `force_insecure` prompt.

Choose the operating system that matches your server, then run the complete command block in a terminal.

<details> <summary><b>Ubuntu / Debian</b></summary>

  ```bash
  sudo apt update && sudo apt install git python3 -y && \
  git clone https://github.com/stlity/Xilla && \
  cd Xilla && \
  python3 -m venv .venv && \
  source .venv/bin/activate && \
  pip install -r requirements.txt && \
  python3 -m xilla
  ```
</details>

<details>
<summary><b>Fedora</b></summary>
  
  ```bash
  sudo dnf update -y && sudo dnf install git python3 -y && \
  git clone https://github.com/stlity/Xilla && \
  cd Xilla && \
  python3 -m venv .venv && \
  source .venv/bin/activate && \
  python3 -m pip install -r requirements.txt && \
  python3 -m xilla
  ```
</details>

<details>
<summary><b>Arch Linux</b></summary>
  
```bash
sudo pacman -Syu --noconfirm && sudo pacman -S git python --noconfirm --needed && \
git clone https://github.com/stlity/Xilla && \
cd Xilla && \
python3 -m venv .venv && \
source .venv/bin/activate && \
python3 -m pip install -r requirements.txt && \
python3 -m xilla
```
</details>



### Other environments

<details>
  <summary><b>WSL(Windows)</b></summary>

  > **⚠️ WARNING: Can be unstable!**

  1. **Download WSL.** For this open window PowerShell with admin rights and write in console 
  ```powershell
  wsl --install -d Ubuntu-22.04
  ```
  
  > *⚠️For install beed Windows 10 build 2004 or Windows 11 of any version and PC with virtualization support.*
  > *For installation on earlier OS, please refer to this [page](https://learn.microsoft.com/ru-ru/windows/wsl/install-manual).*
  
  2. **Restart PC and start programm Ubuntu 22.04.x**
  3. **Enter this command(RMB):** 
  ```bash
  curl -Ss https://bootstrap.pypa.io/get-pip.py | python3
  ```
  > *⚠️ If yellow warnings appear, enter export PATH="/home/username/.local/bin:$PATH" replacing /home/username/.local/bin with the path mentioned in the message*
  
  4. **Enter this command(RMB):**
  ```bash
  clear && git clone https://github.com/stlity/Xilla && cd Xilla && python3 -m venv .venv && source .venv/bin/activate && pip install -r requirements.txt && python3 -m xilla
  ```
  > **🔗How to get API_ID and API_HASH?:** [Video](https://youtu.be/DcqDA249Lhg?t=24)
  
</details>

<details>
  <summary><b>Phone(Userland)</b></summary>
  
  1. <b>Install UserLAnd from</b> <a href="https://play.google.com/store/apps/details?id=tech.ula">the link</a>
  2. <b>Open it, choose Ubuntu —&gt; Minimal —&gt; Terminal</b>
  3. <b>Wait for the distribution to install, you can pour some tea</b> 
  4. <b>After successful installation, a terminal will open in front of you, write there:</b>
    
  ```bash
  sudo apt update && sudo apt upgrade -y && sudo apt install python3 git python3-pip -y && git clone https://github.com/stlity/Xilla && cd Xilla && python3 -m venv .venv && source .venv/bin/activate && sudo pip install -r requirements.txt && python3 -m xilla
  ```

5. <b>At the end of the installation, a link will appear, follow it and enter your account details to log in.</b>
> **Voila! You have installed Xilla on UserLAnd.**
</details>

### Hosting model

Xilla is designed for **self-hosted deployment**. Run it on a VPS, VDS, container host or local Linux environment where you control the data directory, session files and environment variables.

## Migrating from Heroku to Xilla

Xilla includes a compatibility migration for existing Heroku installations. It runs automatically during startup and preserves existing JSON- or Redis-backed data where the same data root and settings are supplied.

> **Important:** Stop the old Heroku instance before starting Xilla. Do not run both instances against the same session files or `REDIS_URL` at the same time.

### Migration checklist

1. **Stop Heroku and create a backup.** Back up the entire Heroku data root, including `config.json`, every `config-*.json` file, `*.session` and `*.session-journal` files, the `sessions/` and `loaded_modules/` directories, and `api_token.txt` if it exists. If the installation uses Redis, also create a backup of the Redis database or snapshot used by `REDIS_URL`.
2. **Install Xilla** using the instructions above. Keep the backup until you have confirmed that the new instance starts and the account data is available.
3. **Copy the existing data into the Xilla data root.** For a regular installation this is the Xilla project directory. For Docker, use the mounted `/data` directory. You can select the data root explicitly with `--data-root /path/to/data`.
4. **Start Xilla once with the same account and environment settings.** Xilla automatically converts legacy database namespaces such as `heroku.*`, `hikka.*`, and `legacy.*` to the current `xilla.*` namespace. Existing `config-*.json` files keep their names and do not need to be renamed manually.
5. **Allow the first startup to finish.** Legacy root-level files named `heroku-*.session` or `heroku-*.session-journal` are moved into the `sessions/` directory and renamed to the corresponding `xilla-*` names. An existing `heroku-userbot` content channel is reused and renamed to `xilla-userbot` when Telegram permissions allow it.
6. **Verify the migration.** Confirm that the expected account is listed, modules load correctly, and the content channel and database-backed settings are available. After verification, keep the backup in a safe place before deleting the old installation.

If the migration fails, stop Xilla and restore the data root and Redis snapshot from the backup. Do not delete the original Heroku files until the Xilla instance has been verified.


## Highlights

<details>
  <summary><b>🔒 Automatic Database Backuper</b></summary>
  <img src="https://user-images.githubusercontent.com/36935426/202905566-964d2904-f3ce-4a14-8f05-0e7840e1b306.png" width="400">
</details>

<details>
  <summary><b>👋 Welcome Installation Screens</b></summary>
  <img src="https://user-images.githubusercontent.com/36935426/202905720-6319993b-697c-4b09-a194-209c110c79fd.png" width="300">
  <img src="https://user-images.githubusercontent.com/36935426/202905746-2a511129-0208-4581-bb27-7539bd7b53c9.png" width="300">
</details>

---

## Capabilities

| Area | What Xilla provides |
|---|---|
| **Telegram compatibility** | Support for current Telegram features, including forums |
| **Control surface** | A redesigned `.help` for discovering modules and `.cfg` for interactive configuration |
| **Modularity** | Core modules plus externally loaded modules and libraries |
| **Continuity** | Compatibility paths for existing Heroku, FTG, GeekTG and Hikka module ecosystems |
| **Inline interactions** | Forms, galleries and lists for richer module flows |
| **Self-hosting** | A deployment model that keeps configuration and sessions under your control |

---

## Requirements

- **Python 3.10+**
- **API Credentials** from [Telegram Apps](https://my.telegram.org/apps)

---

## Documentation

| Resource | Use it for |
|---|---|
| [Installation instructions](#installation) | Starting a new Xilla instance |
| [Migration checklist](#migrating-from-heroku-to-xilla) | Moving an existing Heroku installation to Xilla |
| [Project source and issues](https://github.com/stlity/Xilla) | Reviewing code, reporting issues and contributing |

---

## Support

Use [GitHub Issues](https://github.com/stlity/Xilla/issues) to report reproducible problems or suggest improvements. Include the Xilla version, environment, safe-to-share logs and the steps needed to reproduce the issue.

---

## Usage notice

> This project is provided as-is. The developer takes **NO responsibility** for:
> - Account bans or restrictions
> - Message deletions by Telegram
> - Security issues from scam modules
> - Session leaks from malicious modules
>
> **Security Recommendations:**
> - Enable `.api_fw_protection`
> - Avoid installing many modules at once
> - Review [Telegram's Terms](https://core.telegram.org/api/terms)

---

## Acknowledgements

- [**Hikari**](https://gitlab.com/hikariatama) for Hikka (project foundation)
- [**Lonami**](https://t.me/lonami) for Telethon (Heroku-TL backbone)
