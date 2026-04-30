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
You can download the latest Munipack Flatpak bundle manually from the [releases tab](https://github.com/martin-spacek/Munipack-flatpak/releases) or by running the following command in your terminal:
```bash
wget https://github.com/martin-spacek/Munipack-flatpak/releases/latest/download/cz.muni.physics.munipack.flatpak
```
To install the bundle, run the following command from the directory where the file is located:
```bash
flatpak install --user cz.muni.physics.munipack-x86_64.flatpak
```

> [!NOTE]
> Munipack Flatpak only has permission to access your home folder by default. You can change these sandbox permissions using the `flatpak override` command or via a GUI tool like Flatseal.



## Running commands

### File Browser
Flatpak should automatically create a desktop entry for the file browser in your system app menu. If you prefer opening via CLI, use:
```bash
flatpak run --command=xmunipack cz.muni.physics.munipack
```
### File Viewer
To directly open a specific FITS file in the viewer, use:
```bash
flatpak run --command=xmunipack cz.muni.physics.munipack IMG_5807.fits
```
### Command-line interface
To use the command-line tools for processing, run:
```bash
flatpak run --command=munipack cz.muni.physics.munipack dark image.fits
```
## Command aliases
If you'd like to use the commands exactly as they are written in the official [Munipack guide](https://munipack.physics.muni.cz/guide.html), you need to add aliases to your .bashrc:
1. Open your .bashrc with your preferred editor, e.g.:
    ```bash
    nano ~/.bashrc
    ```
    
2. Add these lines to the end of the file:
    ```
    # Aliases for Munipack-flatpak
    alias xmunipack='flatpak run --command=xmunipack cz.muni.physics.munipack'
    alias munipack='flatpak run --command=munipack cz.muni.physics.munipack'
    ```
    
3. Load the updated .bashrc file with:
    ```bash
    source ~/.bashrc
    ```
