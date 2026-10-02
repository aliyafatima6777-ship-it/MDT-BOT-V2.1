# 🚀 MineCloud VPS Management

<p align="center">
<strong>Discord VPS Management Bot</strong><br> Manage Linux VPS/LXC
infrastructure directly from Discord.
</p>
<p align="center">
<img src="https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python" alt="Python">
<img src="https://img.shields.io/badge/Discord-Bot-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord">
<img src="https://img.shields.io/badge/Linux-Supported-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux">
<img src="https://img.shields.io/badge/LXC-Supported-333333?style=for-the-badge" alt="LXC">
</p>

------------------------------------------------------------------------

## ✨ Features

- 🖥️ VPS management from Discord
- 📊 VPS stats, uptime, processes and logs
- 🔄 Restart / stop / status controls
- 🔐 VPS password reset
- 🌐 VPS network information
- 🔌 TCP/UDP port forwarding
- 🤝 Share VPS access with other users
- 🌐 Multi-node management
- 📦 LXC container management
- 💾 Database backup and port repair
- ⏰ VPS expiration and renewal
- 🛡️ Admin and Main Admin permissions
- 🚀 Self-service `!deploy`
- 🎁 Invite-based VPS reward with confirmation

------------------------------------------------------------------------

# 📚 Commands

> **Important:** These are the commands implemented in the current bot
> code. The bot uses the configured prefix; the examples below use `!`.

## 👤 User Commands

``` text
!ping
!uptime
!myvps
!manage [@user]
!share-user @user <vps_number>
!share-ruser @user <vps_number>
!manage-shared @owner <vps_number>
```

| Command                              | Description                                          |
|--------------------------------------|------------------------------------------------------|
| `1ping`                              | Check bot latency                                    |
| `1uptime`                            | Show host uptime                                     |
| `1myvps`                             | List your VPS                                        |
| `1manage [@user]`                    | Manage your VPS; admin can manage another user’s VPS |
| `1share-user @user <vps_number>`     | Share VPS access                                     |
| `1share-ruser @user <vps_number>`    | Revoke shared VPS access                             |
| `1manage-shared @owner <vps_number>` | Manage a shared VPS                                  |

------------------------------------------------------------------------

## 🖥️ VPS Management

``` text
1myvps
1vpsinfo [vps-id]
1vps-stats <vps-id>
1vps-uptime <vps-id>
1vps-processes <vps-id>
1vps-logs <vps-id> [lines]
1restart-vps <vps-id>
1clone-vps <vps-id> [new_name]
1vps-password <vps-id>
1vps-network <vps-id>
1status <vps-id>
```

| Command                          | Description                    |
|----------------------------------|--------------------------------|
| `1vpsinfo [vps-id]`              | Get VPS information            |
| `1vps-stats <vps-id>`            | Get VPS resource statistics    |
| `1vps-uptime <vps-id>`           | Get VPS uptime                 |
| `1vps-processes <vps-id>`        | List VPS processes             |
| `1vps-logs <vps-id> [lines]`     | View VPS logs                  |
| `1restart-vps <vps-id>`          | Restart VPS                    |
| `1clone-vps <vps-id> [new_name]` | Clone VPS                      |
| `1vps-password <vps-id>`         | Get/reset VPS root password    |
| `1vps-network <vps-id>`          | Show VPS network configuration |
| `1status <vps-id>`               | Show running/stopped status    |

------------------------------------------------------------------------

## 🔌 Port Forwarding

``` text
1ports add <vps_num> <port>
1ports list
1ports remove <id>

1ports-add-user <amount> @user
1ports-remove-user <amount> @user
1ports-revoke <id>
```

Supports TCP/UDP port-forward management.

------------------------------------------------------------------------

## ⚙️ System Commands

``` text
1serverstats
1resource-check
1cpu-monitor <status|enable|disable>
1thresholds
1set-threshold <cpu> <ram>
1set-status <type> <name>
```

------------------------------------------------------------------------

## 🌐 Node Management — Admin

``` text
1node create
1node list
1node status <id>
1node edit <id>
1node regen-key <id>
1node delete <id>
1node migrate <from> <to>
1lxc-list [node_id]

```

------------------------------------------------------------------------

# 🛡️ Admin Commands

``` text
1lxc-list
1create <ram_gb> <cpu_cores> <disk_gb> @user [expiry_days]
1delete-vps @user <vps-id> [reason]
1add-resources <vps-id> [ram] [cpu] [disk]
1resize-vps <vps-id> [ram] [cpu] [disk]
1suspend-vps <vps-id> [reason]
1unsuspend-vps <vps-id>
1suspension-logs [vps-id]
1whitelist-vps <vps-id> <add|remove>
1userinfo @user
1list-all
1exec <vps-id> <command>
1stop-vps-all
1migrate-vps <vps-id> <pool>
1vps-network <vps-id> <action> [value]
1apply-permissions <vps-id>
1vps-password <vps-id>
1node-check <node_id>
1status <vps-id>
1status-summary
1repair-ports
1resource-check
```

### Admin command details

| Command                                     | Purpose                              |
|---------------------------------------------|--------------------------------------|
| `1create <ram> <cpu> <disk> @user [expiry]` | Create a VPS and select its OS       |
| `1delete-vps @user <vps-id> [reason]`       | Delete a user’s VPS                  |
| `1add-resources ...`                        | Add resources                        |
| `1resize-vps ...`                           | Resize VPS resources                 |
| `1suspend-vps ...`                          | Suspend a VPS                        |
| `1unsuspend-vps ...`                        | Unsuspend a VPS                      |
| `1suspension-logs ...`                      | View suspension history              |
| `1whitelist-vps ...`                        | Add/remove auto-suspension exemption |
| `1userinfo @user`                           | View user information                |
| `1list-all`                                 | List all VPS                         |
| `1exec <vps-id> <command>`                  | Execute a command inside a VPS       |
| `1stop-vps-all`                             | Stop all VPS                         |
| `1migrate-vps ...`                          | Migrate VPS storage pool             |
| `1apply-permissions ...`                    | Apply Docker-ready VPS permissions   |
| `1node-check <node_id>`                     | Check node health                    |
| `1status-summary`                           | VPS status summary                   |
| `1repair-ports`                             | Repair port forwarding               |
| `1resource-check`                           | Check high-resource VPS              |

------------------------------------------------------------------------

## ⏰ VPS Expiration — Admin

``` text
1set-expiration <vps-id> <days>
1renew-vps <vps-id> [days]
1vps-expiration [vps-id]
```

Expired VPS can be automatically suspended by the expiration monitor.

------------------------------------------------------------------------

## 🔧 Maintenance & Monitoring — Admin

``` text
1cpu-monitor <status|enable|disable>
1backup-db
1repair-ports
1node-check <node_id>
1resource-check
```

------------------------------------------------------------------------

## 👑 Main Admin Commands

``` text
1admin-add @user
1admin-remove @user
1admin-list
```

Only the configured Main Admin can use these commands.

------------------------------------------------------------------------

# 🤖 Bot Commands

``` text
1help
1quickhelp
1help-search <search_term>
1about
1commands
1stats
1info @user
```

### Command aliases

``` text
1commands  → Help menu
1stats     → Server statistics (Admin)
1info @user → User information (Admin)
```

----------------------------------------------------------------------

# 🎁 Invite VPS Reward

The current code contains the invite reward command:

``` text
1claim
```

The user must have enough valid invites, choose an unlocked plan, and
**confirm the plan before VPS creation**.

### Reward tiers

| Valid Invites |   RAM |     CPU |  Disk |
|--------------:|------:|--------:|------:|
|             2 |  4 GB | 2 Cores | 20 GB |
|             4 |  8 GB | 4 Cores | 35 GB |
|             8 | 16 GB | 6 Cores | 40 GB |
|            16 | 32 GB | 8 Cores | 80 GB |

------------------------------------------------------------------------

# 🧩 `1manage`

The management interface handles VPS actions through Discord
buttons/menus.

Typical controls include:

``` text
▶ Start
⏸ Stop
🔄 Restart
🔑 SSH / Password
📊 Live Stats
📁 File Manager
🖥️ Proxmox Console
🌐 Network
📜 Logs
Logs
```

The exact buttons shown depend on the current bot implementation and VPS
configuration.

------------------------------------------------------------------------

# 📦 Installation

``` bash
git clone https://github.com/aliyafatima6777-ship-it/MDT-BOT-V2.1.git
cd MDT-BOT-V2.1

python3 -m venv .venv
source .venv/bin/activate

python3 -m pip install -r requirements.txt
```

Type `nano .env` 

``` env
DISCORD_TOKEN=your_discord_bot_token
MAIN ADMIN ID = YOUR ADMIN ID
```

Start:

``` bash
source .venv/bin/activate
python3 bot_2.py
```

------------------------------------------------------------------------

# 🔁 24/7 Systemd

Example:

``` ini
[Unit]
Description=MineCloud Discord VPS Bot
After=network.target

[Service]
Type=simple
WorkingDirectory=/root/MineCloud
ExecStart=/root/MineCloud/.venv/bin/python /root/MineCloud/bot_2.py
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

Then:

``` bash
sudo systemctl daemon-reload
sudo systemctl enable minecloud
sudo systemctl start minecloud
sudo systemctl status minecloud
```

Logs:

``` bash
journalctl -u minecloud -f
```

------------------------------------------------------------------------

# 🔐 Security

Never upload these to GitHub:

``` text
.env
Discord Bot Token
Proxmox password
API keys
Private SSH keys
Private panel credentials
```

Use `.gitignore`:

``` gitignore
.env
.venv/
__pycache__/
*.pyc
*.db
*.db-wal
*.db-shm
```

------------------------------------------------------------------------

# 👨‍💻 Credits

**Created by ChatGPT × lahis_g**

------------------------------------------------------------------------

<p align="center">
☁️ <strong>MineCloud VPS Management</strong><br> <sub>Manage your VPS
directly from Discord.</sub>
