# Keep systemd working on WSL2.

## Downgrade systemd.

### Date: 2023/12/19.

* Downgrade systemd to version 249.11-0ubuntu3.9.

### Download requirements.

```console
wget -c https://launchpadlibrarian.net/657332829/udev_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332813/libnss-mymachines_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332815/libnss-systemd_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332816/libpam-systemd_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332818/libudev1_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332798/libudev-dev_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332827/systemd-timesyncd_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332808/systemd-sysv_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332819/systemd-container_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332817/libsystemd0_249.11-0ubuntu3.9_amd64.deb
wget -c https://launchpadlibrarian.net/657332828/systemd_249.11-0ubuntu3.9_amd64.deb
```

### Install each one, checking order.

```console
sudo dpkg -i udev_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i libnss-mymachines_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i libnss-systemd_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i libpam-systemd_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i libudev1_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i libudev-dev_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i systemd-timesyncd_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i systemd-sysv_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i systemd-container_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i libsystemd0_249.11-0ubuntu3.9_amd64.deb
sudo dpkg -i systemd_249.11-0ubuntu3.9_amd64.deb
```

### Fixing this packages by apt.

```console
sudo apt-mark hold libnss-mymachines libnss-systemd libpam-systemd libsystemd0 libudev-dev libudev1 systemd systemd-container systemd-sysv systemd-timesyncd udev
```

## Downgrade WSL itself.

### Download requirements.

```console
curl -sL "https://objects.githubusercontent.com/github-production-release-asset-2e65be/55626935/4efc2cb8-f296-4f0c-9a11-d8edfb5e4c6b?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20231212%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20231212T154719Z&X-Amz-Expires=300&X-Amz-Signature=e1252aa852648459bddb8178afaf5bbf51835727800b90989bf946e57c1c5cfd&X-Amz-SignedHeaders=host&actor_id=5187038&key_id=0&repo_id=55626935&response-content-disposition=attachment%3B%20filename%3Dwsl.2.0.4.0.x64.msi&response-content-type=application%2Foctet-stream" -o wsl.2.0.4.0.x64.msi& -C -
```

### Install with admin console.