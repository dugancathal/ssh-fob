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

## Backups

Because this drive contains information that you probably don't want to lose, you might be interested in a backup strategy.
Personally, I created an encrypted DMG that I store in [keybase](keybase.io).
The command for creating that DMG (after mounting your volume) is:

```
echo -n "$PASSWORD" | hdiutil create -encryption -stdinpass -srcfolder /Volumes/$YOUR_VOLUME_NAME/ ~/$ENCRYPTED_DMG_NAME.dmg
```

You can also not do the `echo` voodoo at the beginning and the command will prompt you for a password.

With the DMG created, you can attach it as a volume using:

```
hdiutil attach ~/$ENCRYPTED_DMG_NAME.dmg
```

And detach said volume with:

```
hdiutil detach $DISK_VOLUME # You'll have to look this up.
```
