# dmi2png+

Unpacks a BYOND "DMI" file into (A)PNGs.

Improved version of https://github.com/liambaloh/DMI2PNG
for command-line use and APNG support.

## What this does

This software unpacks DMI files into individual images, one for each icon state
and direction.

Animated sprites are compiled into an APNG (animated PNG). States with multiple
directions will be placed into a folder named after the state.

If an icon state is duplicated (or missing), this script will append a number
or use "(unnamed)", respectively.

Currently, it is not possible to turn PNGs back into their component DMI files.

## Instructions

You can either install PHP locally or use a pre-build Docker image with all the dependencies sorted out (if you do not wish to install PHP).

### Using PHP

You will need command-line access, an installation of php, and some libraries
like php-gd.

Navigate to the directory containing this repository and run:

    php index.php [path to DMI file or directory]

If a directory is given, it will recursively convert DMI files in that
directory. If a single file is given, it will just convert that single file.

Example:

- test.dmi
  - human (4 directions)
  - robot (animated)

After running, it will write the following folders and files:

- test/
  - human/
    - human-dir1.png
    - human-dir2.png
    - etc.
  - robot.png

The new folder will be in the same folder as the DMI was.

### Using Docker

Same as above, but you can use a pre-made container with PHP and php-gd preinstalled and ready to use, just mount your target path as a volume:

```
docker run -it --rm hamcha/dmi2png -v </path/to/dmi/files>:/in /in
```

You can also build the image yourself with the `Dockerfile` in this repo.

## Credits

- Forked from https://github.com/liambaloh/DMI2PNG (GPL-3.0)
- Animated PNG Creator, version 1.6.2 (LGPL)
- PNGMetadataExtractor class, from MediaWiki

## License

GPL-3.0. See "LICENSE" file for details.
