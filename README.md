# kshook-wine
A script for setting up and injecting [kshook](https://github.com/emskye96/kshook) into SOUND VOLTEX EXCEED GEAR KONASTE/コナステ running in a WINE environment on Linux.

[What is SDVX KONASTE?](https://www.sdvx.org/en/setup/konasute#intro)

kshook is a network forwarder for scores obtained on SDVX KONASTE, and is primarily used for uploading obtained scores to [Tachi](https://github.com/zkrising/Tachi) instances (such as Kamaitachi)

> [!IMPORTANT]
> kshook-wine assumes that you already have SDVX KONASTE installed and it is in a playable state. If you haven't already done this, I suggest using the [konaste-linux](https://github.com/mizztgc/konaste-linux) which streamlines WINE setup and launching

Download the `kshook-wine` script directly from this repository

Alternatively if you are on an Arch-based operating system you can also download the script through the AUR
```bash
yay -S kshook-wine
```

## Setup
An interactive setup tool is available via running
```bash
kshook-wine init
```
The init script can help you download and move the necessary components for injection ([nefarius/Injector](https://github.com/nefarius/Injector) and kshook itself)

This process is the same as what you need to do if you were using `kshook` on Windows (in terms of where files need to be), except `kshook.exe` is not used to launch the game.

## Usage
If you have already completed the init script, run `kshook-wine` with no additional parameters
```bash
kshook-wine
```
The script will now wait for SDVX KONASTE to launch

Launch SDVX KONASTE how you would normally do so. If you are using [konaste-linux](https://github.com/mizztgc/konaste-linux), then this would be
`konaste sdvx` along with any other additional arguments you use. Continue past the launcher and start the game.

Once the game window actually opens, `kshook-wine` should detect that the game has launched and will inject `kshook.dll` for you using `Injector.exe`. If injection is successful then your score will upload at the end of each track played.

Although there is no command output after injection, you can check `kshook.log` in the folder where `kshook.dll` is to debug any potential upload errors.

## Additional Notes
- If you for some reason made modifications to how the SDVX launcher loads the game, `kshook-wine` identifies the game has launched through `ps aux | grep -i "sv6c.exe"`
- The configuration file generated in the init script can be found at `$HOME/.config/kshook-wine/config`
- You may also directly pass parameters to override the configured options, run with `--help` to see the parameters needed

## Additional Package Requirements
You likely already have all these packages but they are not standard on all Linux setups
- mktemp
- curl
- unzip
- wine
