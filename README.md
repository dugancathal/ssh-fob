# SSH-FOB

A script for generating an SSH keyfob.

## Usage

```
# Plug in fob
git clone git@github.com:dugancathal/ssh-fob.git
cd ssh-fob
diskutil list # determine your USB fob disk name
bin/setup
```

### Detailed instructions

1. Plug in your USB fob
1. Run `diskutil list` and determine the disk name of the fob.
1. Run `bin/setup` with two arguments, disk name, and new "volume name"
    ```
    bin/setup disk2 dugancathal
    ```
1. Wait awhile
1. Enter a passphrase (and confirm)
1. Specify whether you want to use an existing SSH key, or generate a new one.
1. Profit

## Post-setup Usage

1. Plug fob into new machine
1. Enter passphrase
1. Run `/Volumes/$YOUR_VOLUME_NAME/add-key $NUM_HOURS` to add your SSH key to the machine's ssh-agent for `$NUM_HOURS` hours.
