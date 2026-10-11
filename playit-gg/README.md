# Playit.gg Agent

![Addon Stage](https://img.shields.io/badge/Addon%20stage-ready-green.svg)
![GitHub License](https://img.shields.io/github/license/Uplandjacob/Upland-ha-addons)

![Supports aarch64 Architecture](https://img.shields.io/badge/aarch64-yes-green.svg?style=flat)
![Supports amd64 Architecture](https://img.shields.io/badge/amd64-yes-green.svg?style=flat)
![Supports armhf Architecture](https://img.shields.io/badge/armhf-no-red.svg?style=flat)
![Supports armv7 Architecture](https://img.shields.io/badge/armv7-deprecated-orange.svg)
![Supports i386 Architecture](https://img.shields.io/badge/i386-no-red.svg)

## About

Playit.gg is a global proxy that allows anyone to host a server without port forwarding.
<!-- CSpell: words williamcorsel -->
Original inspiration thanks to the [Benjamin589 PR](https://github.com/williamcorsel/hassio-addons/pull/26) `williamcorsel/hassio-addons` that used the `alex33856/playitgg-docker` image. The Dockerfile for this addon uses the majority of alex33856's Dockerfile.

## Install

<!-- markdownlint-disable MD036 -->
**Add repository**
<!-- markdownlint-enable MD036 -->

[![Add repo](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/meritw/Upland-HA-Addons)

or go to the **Add-on Store -> repositories** and add: <https://github.com/meritw/Upland-HA-Addons>

**Then install:**

Select **Playit.gg Agent** from this repository in the Add-on Store. This fork
builds the image on your Home Assistant machine during installation or update,
so the first install can take several minutes.

## Setup

1. If you don't already have a Playit.gg account, head over to [Playit.gg](https://playit.gg) and sign up.
2. While signed in, open [Create a Docker agent](https://playit.gg/account/agents/new-docker)
   and create an agent. Copy the agent secret key shown on that page (the value
   used for `SECRET_KEY` in the Docker instructions).
3. Install this fork's add-on and open its **Configuration** tab. Paste the key
   into **Playit agent secret key** (`secret_key`) and save.
4. Start or restart the add-on. Check the **Log** tab for
   `playit connected; tunnels loaded`. No claim link is needed with this setup.
5. On the [Playit agents page](https://playit.gg/account/agents), select this
   agent and add your Minecraft tunnel. Use the Minecraft server's address and
   published port on your Home Assistant machine as the local destination.

The YAML configuration looks like this:

```yaml
secret_key: "PASTE_YOUR_AGENT_SECRET_HERE"
```

Enter your real key only in Home Assistant's Configuration tab. The field is
masked in the form and the startup script does not print its value. Save and
restart the add-on whenever you change the key.

An existing `/etc/playit/playit.toml` file is still supported when `secret_key`
is blank. A configured `secret_key` takes precedence over that file. If neither
is available, the log explains how to configure the key instead of waiting for
a setup client.

## Updating this fork

After these changes are merged, check for updates in the Add-on Store and update
to version **1.3.2**. If you installed the upstream repository's add-on, add this
fork's repository and install its copy instead; repository add-ons have separate
identities. Stop the old Playit add-on before starting this copy.
