# How to share Jupyter Notebooks Live

Source: [JupyterLab Realtime Collaboration](https://jupyterlab-realtime-collaboration.readthedocs.io/en/latest/)

```bash
jupyter server --generate-config
jupyter --paths
```

Find the output below `config:` in the paths, usually `~/.jupyter/`.

Then edit the file `jupyter_server_config.py` to include:

```python
c.ServerApp.allow_remote_access = True  # allow access from other computers
c.ServerApp.ip = '0.0.0.0'              # to be accessible from any IP
c.ServerApp.port = 8888                 # or any port you want
c.ServerApp.collaborative = True        # enable real-time collaboration
c.ServerApp.password = ''               # disable password (disabled by default)

## Optional, to use HTTPS instead of HTTP (recommended)
# c.ServerApp.certfile = 'C:/path/to/cert.pem'
# c.ServerApp.keyfile = 'C:/path/to/key.key'
```

Then run:

```bash
jupyter lab
```

In your browser, open the link share button on the top right corner and copy link with token.

Then you need to rewrite the URL to use your computer's IP address instead of `localhost` or `127.0.0.1` or `machine-name`.

For example, if your computer's IP address is `192.168.1.100`, you would change the URL to `http://192.168.1.100:8888/?token=YOUR_TOKEN_HERE`.

To find your computer's IP address, you can use the command prompt and type `ipconfig` (on Windows) or `ifconfig` (on macOS/Linux).
