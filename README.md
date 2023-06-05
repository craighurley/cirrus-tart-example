# cirrus-tart-test

<https://github.com/cirruslabs/tart/>

## Image Management

```sh
tart pull ghcr.io/cirruslabs/macos-ventura-base:latest
```

```sh
tart clone ghcr.io/cirruslabs/macos-ventura-base:latest ventura-base
```

Note: Images and VMs are stored in `~/.tart/`.

## VM Configuring

Get VM configuration:

```sh
tart get ventura-base
```

Set VM configuration options.  Not all arguments need to be present.

```sh
tart set ventura-base --cpu 4 --memory 8192 --display 1600x1200
```

## Running VMs

Run a VM, mount `~/tmp/` with read/write permissions:

```sh
tart run ventura-base --dir="tmp:~/tmp/"
```

Run a VM, mount `~/tmp/` with read-only permissions and launch the native _Screen Sharing_ application to connect to the VM.  Copy+paste to/from the VM is possible when using _Screen Sharing_.

```sh
tart run ventura-base --dir="tmp:~/tmp/:ro" --vnc-experimental
```

Note: The Virtualization.Framework's VNC server (`--vnc-experimental`) results in a visually better display than the default (`--vnc`).

SSH to the VM:

```sh
ssh admin@$(tart ip ventura-base)
```

## cirrus-cli

Validate `.cirrus.yml` file:

```sh
cirrus validate
```

Print output normally to console:

```sh
cirrus run -o simple
```
