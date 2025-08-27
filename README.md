# timer-bot-image

Docker image build repository for the [timer-bot](https://github.com/14rynx/timer-bot) Discord bot.

## Features

- **Multi-architecture support**: Built for both x86_64 (amd64) and ARM64 architectures
- **Automated builds**: GitHub Actions workflow automatically builds and publishes to Docker Hub
- **Version tagging**: Supports semantic versioning and latest tags

## Required Environment Variables

Before running the timer-bot, you need to configure these environment variables:

| Variable | Description | How to Obtain |
|----------|-------------|---------------|
| `CCP_CLIENT_ID` | EVE Online application client ID | [EVE Developers](https://developers.eveonline.com/) - Create application with "Authentication & API Access" |
| `CCP_SECRET_KEY` | EVE Online application secret key | From your EVE Online application settings |
| `CCP_REDIRECT_URI` | OAuth callback URL | Set to `https://yourdomain.com/callback/` in your EVE app |
| `DISCORD_TOKEN` | Discord bot token | [Discord Developer Portal](https://discord.com/developers/applications) - Create application, go to Bot section |

### EVE Online Application Setup

1. Go to [EVE Developers](https://developers.eveonline.com/) and create a new application
2. Set **Application Type** to "Authentication & API Access"
3. Add these **Permissions**:
   - `esi-universe.read_structures.v1`
   - `esi-corporations.read_structures.v1` 
   - `esi-characters.read_notifications.v1`
4. Set **Callback URL** to your domain: `https://yourdomain.com/callback/`

### Discord Bot Setup

1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
2. Create a new application and go to the "Bot" section
3. Reset the token and copy the new one for `DISCORD_TOKEN`
4. Enable the "Message Content Intent" in the Bot section
5. In "OAuth2" section, generate invite URL with "Bot" scope and "Send Messages"/"Read Messages/View Channels" permissions

## Quick Start

```bash
# Pull the latest image
docker pull petdog/timer-bot:latest

# Create environment file
cat > .env << EOF
CCP_CLIENT_ID=your_eve_client_id
CCP_SECRET_KEY=your_eve_secret_key
CCP_REDIRECT_URI=https://yourdomain.com/callback/
DISCORD_TOKEN=your_discord_bot_token
EOF

# Run with environment file
docker run -d --name timer-bot --env-file .env petdog/timer-bot:latest

# Or run with inline environment variables
docker run -d --name timer-bot \
  -e CCP_CLIENT_ID=your_eve_client_id \
  -e CCP_SECRET_KEY=your_eve_secret_key \
  -e CCP_REDIRECT_URI=https://yourdomain.com/callback/ \
  -e DISCORD_TOKEN=your_discord_bot_token \
  petdog/timer-bot:latest
```

### Using Docker Compose

```yaml
version: '3.8'
services:
  timer-bot:
    image: petdog/timer-bot:latest
    container_name: timer-bot
    environment:
      - CCP_CLIENT_ID=${CCP_CLIENT_ID}
      - CCP_SECRET_KEY=${CCP_SECRET_KEY}
      - CCP_REDIRECT_URI=${CCP_REDIRECT_URI}
      - DISCORD_TOKEN=${DISCORD_TOKEN}
    restart: unless-stopped
```


## Original Project

This is a containerized build repository for the original [timer-bot](https://github.com/14rynx/timer-bot) project by 14rynx - a Discord bot for Eve Online structure notifications.
