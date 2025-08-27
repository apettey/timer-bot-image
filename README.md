# timer-bot-image

Docker image build repository for the [timer-bot](https://github.com/14rynx/timer-bot) Discord bot.

## Features

- **Multi-architecture support**: Built for both x86_64 (amd64) and ARM64 architectures
- **Automated builds**: GitHub Actions workflow automatically builds and publishes to Docker Hub
- **Version tagging**: Supports semantic versioning and latest tags

## Quick Start

```bash
# Pull the latest image
docker pull petdog/timer-bot:latest

# Run the container
docker run -e CCP_CLIENT_ID={client_id} -e CCP_SECRET_KEY={your_secret} -e CCP_REDIRECT_URI={redirect_uri} -e DISCORD_TOKEN={discord_token} petdog/timer-bot:latest
```

## Setup

See [DOCKER_SETUP.md](./DOCKER_SETUP.md) for detailed instructions on:
- Setting up GitHub secrets for Docker Hub publishing
- Workflow triggers and configuration
- Multi-architecture build details

## Original Project

This is a containerized build repository for the original [timer-bot](https://github.com/14rynx/timer-bot) project by 14rynx - a Discord bot for Eve Online structure notifications.
