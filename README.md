# myarm

Manage Rasperry Pi emulation with QEMU

## Installation

Two basic ways of installation are available,
in both cases make sure to use directory available via `$PATH`.

1. Download the script to `~/bin`:

        curl -L https://raw.github.com/mpapis/myarm/master/bin/myarm -o ~/bin/myarm
        chmod +x ~/bin/myarm

    To update repeat the steps.

2. Clone repository and link script to `~/bin`:

        mkdir -p ~/projects
        git clone https://github.com/mpapis/myarm.git ~/projects/myarm
        ln -s ~/projects/myarm/bin/myarm ~/bin/myarm

    To update:

        cd ~/projects/myarm
        git pull

The second option is useful in development when changing the script.

## Usage

### Prepare

Create a new virtual machine based on Rasperry Pi image:

    myarm prepare [URL [name]]

- `URL`  - url to online image from http://downloads.raspberrypi.org/images/raspbian/
- `name` - name of the virtual machine directory

Both can be omitted and will b auto detected, use `""`(empty string) for `URL` if only name is important.

### Start

Few ways of starting are available:

    myarm start [ssh|gui|console]

- `ssh` - start in backgroud, wait for ssh and connect,
- `gui` - start in background with the GUI open to the machine,
- `console` - start in forground with open console to the server.
- with no parameter will just start in background,
  you need to wait a bit for the machine to boot, it can take eve few minutes.

### Stop

Stop the running virtual machine:

    myarm stop

### Status

Show if the virtual machine is running, returns nonzero status if it's not running:

    myarm status

### SSH

Allow connecting to the virtual machine:

    myarm ssh

### SCP

Allow upload / download of files:

    myarm scp ...

Use like standard scp, use 'pi@localhost' for the virtual machine

## Configuration files

Standard virtual machine is a directory with file `.myarm` which contains:

    IMAGE=path_to_image.img
    PORT=forward_port
    CPU=arm_cpu
    RAM=machine_ram

Only `IMAGE` is required, for rest defaults will be used if not set:

    PORT="5022"
    CPU="arm1176"
    RAM="256"

## Reporting problems

https://github.com/mpapis/myarm/issues
