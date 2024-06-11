## How to mount Google Drive on Linux:
- https://www.xmodulo.com/mount-google-drive-linux.html

## Repo:
- https://github.com/astrada/google-drive-ocamlfuse


## Automount quickguide

### 1. Create mount script:

```shell
sudo nano /usr/local/bin/gdrive_mount.sh
```

Edit with your labels and folders:

```shell
#!/bin/bash

~/.opam/default/bin/google-drive-ocamlfuse -label default ~/googledrive
~/.opam/default/bin/google-drive-ocamlfuse -label other_label ~/other_folder
```

Make it executable:
```
sudo chmod +x /usr/local/bin/gdrive_mount.sh
```

### 2. Create unmount script:

```shell
sudo nano /usr/local/bin/gdrive_unmount.sh
```

Edit with your folders:

```shell
#!/bin/bash

fusermount -u ~/googledrive
fusermount -u ~/other_folder
```

Make it executable:
```
sudo chmod +x /usr/local/bin/gdrive_unmount.sh
```


### 3. Create linux systemd service:

```shell
sudo nano /etc/systemd/system/google-drive.service
```

Edit with your user (USER):

```ini
[Unit]
Description=FUSE filesystem over Google Drive
After=network.target

[Service]
User=USER
Group=USER
ExecStart=/usr/local/bin/gdrive_mount.sh
ExecStop=/usr/local/bin/gdrive_unmount.sh
Restart=always
Type=forking

[Install]
WantedBy=multi-user.target
Alias=google-drive.service
```


```shell
# activate service
sudo systemctl daemon-reload

# start service
sudo systemctl start google-drive

# check status
sudo systemctl status google-drive
```