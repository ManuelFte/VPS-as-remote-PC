# Ubuntu server as remote PC

## Description

Turns an Ubuntu 20.04 server into a basic remote PC, with LXQt and access via VNC.

![image](https://github.com/ManuelFte/VPS-as-remote-PC/assets/68722732/9ce618da-1ba4-4cc7-9676-9c9da785cd10)

## Installed software

* LXQt (with Openbox)
* TigerVNC Standalone Server
* Chromium

## Requirements

- Ubuntu 20.04
- At least 4 GB of RAM
- At least 20 GB of storage

## Optional modes

- `--scratch / -sc` - When the script is run on a new server. Adjusts the clock and sets up a password for the current user.
- `--dns / -dn` - Sets up OpenDNS nameservers (more options available in `resolved.conf`).
- `--full / -fl` - Does all of the above.


## Usage

Clone the repository:

```
git clone https://github.com/ManuelFte/Ubuntu-server-as-remote-PC
```

Enter the script's directory:

```
cd Ubuntu-server-as-remote-PC
```

[Optional] Open `main.sh` and set the correct timezone in the user variables:

```
nano main.sh
```

Run the script:

```
bash main.sh [<mode(s)>]
```

After the script has finished, type one of these commands in the **client** machine to connect:

a) If you're using login via SSH key:

```
ssh -i ~/.ssh/id_rsa -L 7000:localhost:5900 -N -v <user>@<IP>

```

b) If you're using login via password:

```
ssh -L 7000:localhost:5900 -N -v <user>@<IP>
```

Then, also from the **client** machine, use a VNC program like TigerVNC to connect to `localhost:7000` (on Linux you can use `vncviewer localhost:7000`).