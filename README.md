# scpd-runner

A multi-arch Docker image providing a Java development environment for CI/CD pipelines.

## What's Included

- **Ubuntu** (latest) base image
- **Liberica JDK 21** (21.0.10) via SDKMAN!
- CLI tools: `curl`, `tar`, `zip`, `unzip`, `jq`, `git`, `gh`
- Maven `settings.xml` pre-configured at `/root/.m2/`

## Usage

```bash
docker pull ghcr.io/dashaun/scpd-runner:latest
docker run -it ghcr.io/dashaun/scpd-runner:latest
```

Initialize SDKMAN! inside the container before using Java or Maven:

```bash
source /root/.sdkman/bin/sdkman-init.sh
```

## Available Image Tags

| Tag | Architecture |
|---|---|
| `latest` | Multi-arch manifest (amd64 + arm64) |
| `linux-amd64` | linux/amd64 |
| `linux-arm64` | linux/arm64 |

## Building Locally

```bash
docker build -t scpd-runner .
```

## CI/CD

A GitHub Actions workflow builds and publishes images on every push to `main`. The `linux-amd64` and `linux-arm64` images are built in parallel, then combined into a multi-arch manifest tagged as `latest`. Images are published to GitHub Container Registry (GHCR).

Pull requests trigger builds on both architectures without pushing.

## License

[Apache License 2.0](LICENSE)
