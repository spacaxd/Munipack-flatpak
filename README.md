# Munipack-flatpak
Repository for distribution of Munipack via Flatpak. 

**What is Flatpak?**
Flatpak is a universal package management system that bundles the application with all its necessary dependencies (like specific versions of system libraries) inside a secure sandbox. This ensures Munipack runs flawlessly on any Linux distribution without library conflicts or "missing dependency" errors.

## Install

**1. Prerequisites**
Ensure you have Flatpak installed on your system. You also need to enable the Flathub repository, as Munipack relies on its base runtime to function:
```bash
flatpak remote-add --user --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
2. Download the bundle Download cz.muni.physics.munipack.flatpak from the build folder, or directly via CLI:

wget [https://github.com/martin-spacek/Munipack-flatpak/raw/main/build/cz.muni.physics.munipack.flatpak](https://github.com/martin-spacek/Munipack-flatpak/raw/main/build/cz.muni.physics.munipack.flatpak)

3. Install Install the downloaded Flatpak bundle from the directory where it is located:

flatpak install --user cz.muni.physics.munipack.flatpak

    [!NOTE] Munipack Flatpak only has permission to access your home folder by default. You can change these sandboxing permissions using the flatpak override command or via a graphical tool like Flatseal.

Running commands
Graphical User Interface (GUI)

Flatpak should automatically create a desktop entry for the application in your system menu. If you prefer opening the GUI via CLI, use:

flatpak run --command=xmunipack cz.muni.physics.munipack

File Viewer

To directly open a specific FITS file in the viewer, use:

flatpak run --command=xmunipack cz.muni.physics.munipack IMG_5807.fits

Munipack CLI

To use the command-line tools for processing, run:

flatpak run --command=munipack cz.muni.physics.munipack dark image.fits

Command Aliases

If you'd like to use the commands exactly as they are written in the official Munipack guide, you should add these aliases to your .bashrc (or .zshrc):

    Open your .bashrc with your preferred editor, e.g.:

    nano ~/.bashrc

    Add these lines to the end of the file:

    # Aliases for Munipack flatpak
    alias xmunipack='flatpak run --command=xmunipack cz.muni.physics.munipack'
    alias munipack='flatpak run --command=munipack cz.muni.physics.munipack'

    Load the updated .bashrc file with:

    source ~/.bashrc

