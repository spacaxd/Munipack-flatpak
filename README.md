# Munipack-flatpak
Repository for distribution of Munipack via Flatpak. 

**What is Flatpak?**
Flatpak is a universal package management system that bundles the application with all its necessary dependencies (like specific versions of system libraries) inside a secure sandbox. This ensures Munipack runs on any Linux distribution without library conflicts or "missing dependency" errors.


## Prerequisites
Ensure you have Flatpak installed on your system. You also need to enable the official Flathub repository, as Munipack relies on its base runtime to function:
```bash
flatpak remote-add --user --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

## Installation
Download the `cz.muni.physics.munipack.flatpak` bundle from the [build folder](https://github.com/martin-spacek/Munipack-flatpak/tree/main/build), or directly via CLI:
```bash
wget https://github.com/martin-spacek/Munipack-flatpak/raw/main/build/cz.muni.physics.munipack.flatpak
```

Install the downloaded Flatpak bundle from the directory where it is located:
```bash
flatpak install --user cz.muni.physics.munipack.flatpak
```
> [!NOTE]
> Munipack Flatpak only has permission to access your home folder by default. You can change these sandboxing permissions using the flatpak override command or via a graphical tool like Flatseal.



## Running commands
### Graphical User Interface (GUI)

Flatpak should automatically create a desktop entry for the application in your system menu. If you prefer opening the GUI via CLI, use:
```bash
flatpak run --command=xmunipack cz.muni.physics.munipack
```
### File Viewer

To directly open a specific FITS file in the viewer, use:
```bash
flatpak run --command=xmunipack cz.muni.physics.munipack IMG_5807.fits
```
### Munipack CLI

To use the command-line tools for processing, run:
```bash
flatpak run --command=munipack cz.muni.physics.munipack dark image.fits
```
## Command Aliases

If you'd like to use the commands exactly as they are written in the official Munipack guide, you should add these aliases to your .bashrc (or .zshrc):

- Open your .bashrc with your preferred editor, e.g.:
    ```bash
    nano ~/.bashrc
    ```

- Add these lines to the end of the file:
    ```
    # Aliases for Munipack flatpak
    alias xmunipack='flatpak run --command=xmunipack cz.muni.physics.munipack'
    alias munipack='flatpak run --command=munipack cz.muni.physics.munipack'
    ```
    
- Load the updated .bashrc file with:
    ```bash
    source ~/.bashrc
    ```
