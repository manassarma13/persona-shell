# Persona Shell

Personal landing page that acts as a central hub — redirecting visitors to all hosted projects.

## Stack

- **Static HTML/CSS/JS** — no frameworks, no build step
- **Nginx Alpine** — lightweight container (~7MB)
- **Docker** — containerized deployment
- **Caddy** — reverse proxy with auto-TLS on VPS

## Deployment

```bash
# On VPS
git clone <repo-url> persona-shell
cd persona-shell
docker compose up -d --build
```

Then update `/etc/caddy/Caddyfile`:

```caddy
# Root domain → Persona Shell
smgstation.com, www.smgstation.com {
    reverse_proxy localhost:8080
}

# Personal Hub
hub.smgstation.com {
    reverse_proxy localhost:4000
}

# Tech Meemer
memes.smgstation.com {
    reverse_proxy localhost:3069
}
```

Reload Caddy:
```bash
sudo systemctl reload caddy
```
