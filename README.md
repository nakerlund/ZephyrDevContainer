# Zephyr and LwM2M

This project is setup to do everything needed to run the [Zephyr LwM2M Sample](https://docs.zephyrproject.org/latest/samples/net/lwm2m_client/README.html) in QEMU with the [Leshan Demo Server](https://github.com/eclipse-leshan/leshan?tab=readme-ov-file#test-leshan-demos-locally)

## Prerequisites

1. Install VS Code
2. Install Docker (If on Windows or MacOS, use Docker Desktop)

## Instructions

Open this project in VS Code and let it start the dev container.
This will do the following:

- Download and setup Zephyr while building the [DevContainer Dockerfile](.devcontainer/Dockerfile)
- Download and run the [Leshan Demo Server Dockerfile](leshan/Dockerfile)
- Start the DevContainer with VS Code

Leshan should start on its own at [localhost](http://localhost:8080).

### 1. Build lwM2M Sample

- *Terminal 1:*

```bash
west build -b qemu_x86 /west/zephyr/samples/net/lwm2m_client -DCONF_FILE="prj.conf"
```

### 2. Setup network for qemu

Start the net-tools according to the [guide](https://docs.zephyrproject.org/1.13.0/subsystems/networking/qemu_setup.html#basic-setup)

- *Terminal 2:*

```bash
cd /west/tools/net-tools
. loop-socat.sh
```

- *Terminal 3:*

```bash
cd /west/tools/net-tools
sudo bash loop-slip-tap.sh
```

### 3. Run qemu with the build

- *Terminal 4:*

```bash
west build -t run
```
