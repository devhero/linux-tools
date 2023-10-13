When run `docker compose up` and shell returns error:

    error getting credentials - err: exit status 1, out: `error getting credentials - err: exit status 1, out: `no usernames for https://index.docker.io/v1/``

Edit `~/.docker/config.json` changing key `"credsStore"` in `"credStore"`:

    {
      "auths": {},
      "credStore": "desktop",
      "currentContext": "desktop-linux"
    }
