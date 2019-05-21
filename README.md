# pustIt
Rsync abastraction and deployment tool.

## Installation

**Option 1: Install via composer**

```composer require oboxmedia/push-it```

Then you can run it from within your project `php vendor/bin/pushIt -h`

**Option 2: Standalone installation**

```git clone git@github.com:Oboxmedia/pushIt.git```

Then you can run it by invoking the script `php scripts/pushIt -h`

## Quick Start

**Step  1**
Define a .pushIt.conf file in the root of your project

For example:
```
[default]
defaultTarget=app

[app]
source=/path/to/your/staging.project/
destination=/path/to/your/production.project/
excludeFile=/path/to/your/excludeFile.txt
```

**Step 2**
Defaint a excludeFile.txt this will list files to ignore when synching

For example:
```
.git
README.md
wp-content/uploads/
```

**Step 3**
From the root of you project run the sync scripts

`php vendor/bin/pushIt --target app`

## Configuration

Wehn running the pushIt script it will look in the current folder for a `.pushIt.conf` file.  If not found it will work back up the file tree and use the first `.pushIt.conf` file it finds.

Alternatively you can use the `--config` or `-c` option to specify a configuration file.

This file has two types of configuration the `[default]` options, which control some behaviours or the script, it allows to define defaults for different deploy targets.

Deploy targets define a source and destination folder to push.  Each target is defined in a `[target name]` section in the config file.

### default configuration directives

The `[default]` section enable you to define global options that are used in all targets.

**defaultTarget**: allows you to define which target is used by default (when no `--target` or `-t` option is specified.

### Deploy Target configuration directives

**source**: source folder to sync (same as rsync source)
**destination**: destination folder to sync to  (same as rsync destination)
**excludeFile**: text file that contains file patterns to ignore (same as rsync `--exclude-from`)

