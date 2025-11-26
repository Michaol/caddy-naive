# Caddy with NaiveProxy

Caddy server compiled with [NaiveProxy forwardproxy plugin](https://github.com/klzgrad/forwardproxy).

[![Build Caddy with NaiveProxy](https://github.com/Michaol/caddy-naive/actions/workflows/build.yml/badge.svg)](https://github.com/Michaol/caddy-naive/actions/workflows/build.yml)

## Features

- ✅ Latest Caddy version (auto-updated)
- ✅ NaiveProxy forwardproxy plugin
- ✅ Automatic builds via GitHub Actions
- ✅ Multi-architecture support (x64, arm64)
- ✅ SHA256 checksums for verification

## Download

Download the latest release from [Releases](https://github.com/Michaol/caddy-naive/releases/latest).

### Supported Platforms

- Linux x64
- Linux arm64

## Quick Start

### Download and Install

```bash
# Download latest version (x64)
wget https://github.com/Michaol/caddy-naive/releases/latest/download/caddy-linux-amd64

# Rename and make executable
mv caddy-linux-amd64 caddy
chmod +x caddy

# Verify version
./caddy version

# Verify NaiveProxy module
./caddy list-modules | grep forward_proxy
```

### Basic Usage

```bash
# Run with Caddyfile
./caddy run --config Caddyfile

# Start as daemon
./caddy start --config Caddyfile

# Reload configuration
./caddy reload --config Caddyfile
```

## Example Caddyfile

```caddyfile
{
    order forward_proxy before file_server
}

:443, example.com {
    tls me@example.com
    
    forward_proxy {
        basic_auth user pass
        hide_ip
        hide_via
        probe_resistance
    }
    
    file_server {
        root /var/www/html
    }
}
```

## Build from Source

This repository uses GitHub Actions to automatically build Caddy with the NaiveProxy plugin.

### Manual Build

```bash
# Install xcaddy
go install github.com/caddyserver/xcaddy/cmd/xcaddy@latest

# Build Caddy with NaiveProxy
xcaddy build --with github.com/caddyserver/forwardproxy=github.com/klzgrad/forwardproxy@naive

# Verify build
./caddy version
./caddy list-modules | grep forward_proxy
```

## Automated Builds

Builds are triggered:
- **Manually**: Via GitHub Actions workflow dispatch
- **Weekly**: Every Sunday at 00:00 UTC (checks for updates)

## Verification

Each release includes SHA256 checksums. Verify your download:

```bash
# Download checksum file
wget https://github.com/Michaol/caddy-naive/releases/latest/download/checksums.txt

# Verify
sha256sum -c checksums.txt --ignore-missing
```

## Related Projects

- [Caddy](https://github.com/caddyserver/caddy) - Fast and extensible multi-platform HTTP/1-2-3 web server
- [NaiveProxy](https://github.com/klzgrad/naiveproxy) - Make a fortune quietly
- [forwardproxy (naive fork)](https://github.com/klzgrad/forwardproxy) - Forward proxy plugin for Caddy

## License

This project follows the same license as Caddy (Apache 2.0).

## Disclaimer

This is an unofficial build. For official Caddy builds, visit [caddyserver.com](https://caddyserver.com/).
