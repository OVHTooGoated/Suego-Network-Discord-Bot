# Draco Network Bot

A small Discord network utility bot built in Python.

Draco is made for quick checks from inside Discord instead of opening five different tools for basic network information. Type a command, get a clean embed back, and keep moving.

This is a personal project with a simple command style, straightforward code, and no unnecessary framework around it.

## What It Does

### IP lookup

```text
!iplookup 1.1.1.1
```

Looks up public IP information through IP-API, including:

- City
- Country
- Region
- Time zone
- ISP
- Latitude and longitude
- Mobile, proxy, and hosting flags

### WHOIS / RDAP lookup

```text
!whois example.com
```

Requests domain registration data through RDAP and displays the domain status and nameservers.

### Port check

```text
!portcheck example.com 443
```

Checks one host and one port at a time and reports whether the connection is open, closed, or unreachable.

This command is intended for systems you own or have permission to test. It does not scan port ranges.

### HTTP check

```text
!http https://example.com
```

Checks a website and reports:

- HTTP status code
- Response time
- Final URL after redirects

### Host ping

```text
!ping example.com
```

Resolves a hostname and checks TCP reachability on port `443`.

### DNS lookup

```text
!dns example.com
```

Resolves a domain and displays its IPv4 addresses.

## Command List

| Command | What it does |
| --- | --- |
| `!help` | Shows the available commands |
| `!iplookup <ip>` | Looks up public IP information |
| `!whois <domain>` | Gets RDAP domain information |
| `!portcheck <host> <port>` | Checks one specific port |
| `!http <url>` | Checks HTTP status and response time |
| `!ping <host>` | Checks hostname resolution and TCP reachability |
| `!dns <domain>` | Resolves a domain to IPv4 addresses |

## Setup

### Requirements

- Python 3.10 or newer
- A Discord bot application
- Message Content Intent enabled
- `discord.py`
- `requests`
- `python-dotenv`

### Install packages

Open Command Prompt in the project folder:

```cmd
py -m pip install -U discord.py requests python-dotenv
```

### Create the environment file

Create a file named `.env` next to `DracoDiscordBot.py`:

```env
TOKEN=your_discord_bot_token_here
```

The code loads the token with `python-dotenv`, so the token stays outside the Python file.

### Enable the Discord intent

In the Discord Developer Portal:

1. Open your bot application.
2. Go to **Bot**.
3. Find **Privileged Gateway Intents**.
4. Enable **Message Content Intent**.
5. Save the changes.

### Start Draco

```cmd
py DracoDiscordBot.py
```

When it connects, the console prints the bot username and the bot cycles through its status messages.

## Project Layout

```text
DracoDiscordBot/
├── DracoDiscordBot.py
├── .env
└── README.md
```

Keep the real `.env` file private. Before pushing to GitHub, add it to `.gitignore`:

```gitignore
.env
__pycache__/
*.pyc
```

You can also create a safe `.env.example` for the repository:

```env
TOKEN=put_your_token_here
```

## Embed Style

Draco uses two simple embed colors:

- Red for missing arguments and failed requests
- Black for successful results

Network results include the Discord requester in the footer so it is clear who ran the command.

## Notes

The network commands use external services, so a service can occasionally be slow, unavailable, or return incomplete data. The bot should be run with a stable internet connection and a valid Discord token.

Only use network checks against hosts and services you own or are authorized to test. Do not use the bot for denial-of-service activity, credential collection, or unauthorized scanning.

## License

No license has been added yet. Until one is added, all rights are reserved by the project owner.
