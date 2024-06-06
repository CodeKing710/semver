# semver

This handy little script searches for a version file based on the name desired in settings (default is just 'version') and updates the numerics based on semantic versioning (X.Y.Z where X=Major version, Y=Minor version, and Z=Patch version). The general syntax of the version file should be as follows:

name - v0.0.0

Now for this to work and show up properly, you must make sure the EOF is a blank line before the actual EOF character. This is mainly for display purposes as `semver` does not care about whitespace.

Using `semver` is easiest in command mode, but arguments are still supported. Both variants will be shown in the examples. Semver looks for a version file based on the name in settings, maximum depth of 2 subdirectories. If more than one is found the first one found is used. It will then update this file in place.

## Major version updates

Major updates are super simple, just run the following:

```bash
semver major

semver -M # Alternative
```

This will increment the major version number by 1. Please note upon a major version release `semver` takes care of resetting the minor and patch versions to zero.

## Minor version updates

Minor updates are just as easy, you might start to see a theme here of the simplicity of this script.

```bash
semver minor

semver -m # Alt
```

See? Easy. This will increment the minor version number by 1 and reset the patch version to zero, leaving the major version untouched.

## Patch version updates

You can probably guess how easy this one is too :)

```bash
semver patch

semver -p # Alt
```

This will increment the patch version number by 1, leaving the others untouched. It is just a patch afterall

## Configuration

Semver has very little configuration options as it is fairly new and other version styles are generally not ideal for smaller applications, but it does autoupdate. This can be turned off by running;

```bash
semver config au=false

semver -C au=false # Alt
```

Running `semver config list` will list all the current available settings and their values.

If you want to change the default name for the version file, you can run `semver config vfile=NAME`, replacing 'NAME' with the name of the version files you will be working with. You can also dynamically grab a different version file by using the `file` command within `semver`, but this is still a work in progress and is not currently functioning. Also to come is formats so various version formats are supported (alphanumeric styles, etc)

Of course versioning info and help documentation can be found by running `semver version` or `semver help` respectively.
