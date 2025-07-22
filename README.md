# mildman1848/mod-infisical-cli

This mod installs the Infisical CLI into any LinuxServer.io container using S6-overlay, executed during container initialization.

To use this mod, set the environment variable `DOCKER_MODS=mildman1848/mod-infisical-cli` in your container configuration.

If adding multiple mods, separate them with `|`, e.g., `DOCKER_MODS=mildman1848/mod-infisical-cli|linuxserver/mods:universal-git`.

## Usage

Add the following to your Docker Compose or run command:

```yaml
- DOCKER_MODS=mildman1848/mod-infisical-cli
- INFISICAL_TOKEN=your-infisical-token
```

Modify the container's command to use Infisical for secret injection, e.g.:

```bash
command: infisical run --token $INFISICAL_TOKEN -- your-app-start-command
```

The mod runs as a oneshot S6 service during init, installing the CLI with a pinned version for consistency.

See [Infisical Docker Integration](https://infisical.com/docs/integrations/platforms/docker) for details.

## Notes

- Designed for Alpine-based images; adjust for other bases if needed.
- Infisical CLI version: 0.41.94 (check [releases](https://github.com/Infisical/cli/releases) for updates).
- Manage `INFISICAL_TOKEN` securely.

## Building the Mod Image

Build and push to Docker Hub:

```bash
docker build -t mildman1848/mod-infisical-cli .
docker push mildman1848/mod-infisical-cli
```

## About

Docker mod for Infisical CLI installation via S6-overlay.

## License

MIT License

## Footer

© 2025 mildman1848