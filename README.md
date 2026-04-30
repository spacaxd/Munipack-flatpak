# Munipack-flatpak
Repository for distribution of Munipack via Flatpak. 

**What is Flatpak?**
Flatpak is a universal package management system that bundles the application with all its necessary dependencies (like specific versions of system libraries) inside a secure sandbox. This ensures Munipack runs on any Linux distribution without library conflicts or "missing dependency" errors.

> [!WARNING]
> The app id is going to change to `cz.muni.physics.munipack` soon, so if you later reinstall or update Munipack-flatpak, you will have to update the aliases in your .bashrc if you set them now.
> 
> Automatic creation of a desktop entry for the file browser will be added soon.

## Prerequisites
Ensure you have Flatpak installed on your system. You also need to enable the official Flathub repository, as Munipack relies on its base runtime to function:
```bash
flatpak remote-add --user --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

## Installation
You can install the latest Munipack Flatpak bundle by running the following command in your terminal:
```bash
flatpak install --user https://github.com/martin-spacek/Munipack-flatpak/releases/latest/download/cz.muni.physics.munipack.flatpak
```
or by manually downloading the bundle from the releases tab and running the following command from the directory where it is located:
```bash
flatpak install --user cz.muni.physics.munipack.flatpak
```

> [!NOTE]
> Munipack Flatpak only has permission to access your home folder by default. You can change these sandbox permissions using the `flatpak override` command or via a GUI tool like Flatseal.



## Running commands

### File Browser
To open the specialized file browser GUI, use:
```bash
flatpak run --command=xmunipack cz.muni.physics.munipack.xmunipack
```
### File Viewer
To directly open a specific FITS file in the viewer, use:
```bash
flatpak run --command=xmunipack cz.muni.physics.munipack.xmunipack IMG_5807.fits
```
### Command-line interface
To use the command-line tools for processing, run:
```bash
flatpak run --command=munipack cz.muni.physics.munipack.xmunipack dark image.fits
```
## Command aliases
If you'd like to use the commands exactly as they are written in the official [Munipack guide](https://munipack.physics.muni.cz/guide.html), you need to add these aliases to your .bashrc:
1. Open your .bashrc with your preferred editor, e.g.:
    ```bash
    nano ~/.bashrc
    ```
    
2. Add these lines to the end of the file:
    ```
    # Aliases for Munipack-flatpak
    alias xmunipack='flatpak run --command=xmunipack cz.muni.physics.munipack.xmunipack'
    alias munipack='flatpak run --command=munipack cz.muni.physics.munipack.xmunipack'
    ```
    
3. Load the updated .bashrc file with:
    ```bash
    source ~/.bashrc
    ```
