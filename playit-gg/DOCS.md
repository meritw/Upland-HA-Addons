# Configuration

1. Sign into [Playit.gg](https://playit.gg).
2. Open [Create a Docker agent](https://playit.gg/account/agents/new-docker),
   create an agent, and copy its agent secret key. This is the `SECRET_KEY`
   value shown in the Docker instructions; you do not need to run Docker commands.
3. Paste the key into **Playit agent secret key** in this add-on's
   **Configuration** tab, then save and restart the add-on.
4. Check the log for `playit connected; tunnels loaded`.
5. Select the agent on the [agents page](https://playit.gg/account/agents) and
   create a tunnel targeting your Minecraft server's local address and published
   port.

```yaml
secret_key: "PASTE_YOUR_AGENT_SECRET_HERE"
```

Keep the real key in Home Assistant's configuration, not in GitHub. The form
masks this field and the startup script does not log the configured value.
Changes take effect after restarting the add-on.

If you already have a saved `/etc/playit/playit.toml` file, you may leave
`secret_key` blank to use it. Otherwise, a blank key produces a configuration
error in the log. This version does not generate a claim URL at startup.

This fork builds its image on the Home Assistant machine during installation
and updates, which may take several minutes.
