## Curseforge

docker-compose.yml 내용

```yaml
services:
  mc:
    image: docker.io/itzg/minecraft-server
    tty: true
    container_name: mc-srv
    stdin_open: true
    ports:
      - "25565:25565"
    environment:
      EULA: TRUE
      MEMORY: 8G
      TYPE: AUTO_CURSEFORGE
      MODPACK_PLATFORM: AUTO_CURSEFORGE
      CF_API_KEY: $$2a$$10$$yHgkKqbKDYk/11QGVulZzezFMqALTEp2jLBClEe1ZU3eR.it/G4Mu
      CF_PAGE_URL: https://www.curseforge.com/minecraft/modpacks/ciscos-adventure-rpg-ultimate
      ALLOW_FLIGHT: TRUE
      ENFORCE_SECURE_PROFILE: FALSE
      MOTD: Cisco_rpg
      RCON_PASSWORD: m00nlygreat
      JVM_OPTS: "-Dfml.doVersionCheck=false"
    volumes:
      - ./data:/data
    restart: unless-stopped
```

## Modrinth

```yaml
services:
  mc:
    image: docker.io/itzg/minecraft-server
    tty: true
    container_name: cobbleverse
    stdin_open: true
    ports:
      - "25565:25565"
    environment:
      EULA: TRUE
      MEMORY: 12G
      TYPE: MODRINTH
      MODRINTH_MODPACK: cobbleverse
      ALLOW_FLIGHT: TRUE
      ENFORCE_SECURE_PROFILE: FALSE
      MOTD: Cobbleverse
      RCON_PASSWORD: m00nlygreat
      JVM_OPTS: "-Dfml.doVersionCheck=false"
      MODRINTH_EXCLUDE_FILES: |
        cobblemon-ui-tweaks
      MODRINTH_OVERRIDES_EXCLUSIONS: |
        mods/*cobblemon*ui*tweak*
    volumes:
      - ./data:/data
    restart: unless-stopped
```




