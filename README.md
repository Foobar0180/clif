# clif: Bash based CLI Framework

`clif` is an open source framework for building generalised command-line interface (CLI) applications. Create CLIs with a few flags or advanced CLIs that have subcommands.

## Setup

The install walk-through is a step-by-step guide to setting up and configuring `clif`.

## Possible examples

```
$ clif help

$ clif app get-log --log-output /Users/yourusername/Desktop

$ clif app start-device

$ clif deploy create-release --version 1.2.3

$ clif project get-project --no-dependencies
```

## Customizing the CLI
The CLI is designed to make it as simple as possible for you to create _your_ application. To that end, everything that makes it _yours_ can be changed by simply modifying the files in the `command` directory.

### Types of commands

With clif you can create 2 different CLI types, `single` and `multi`.

Single CLIs are like `pwd` or `touch`. They can accept arguments and flags. Single CLIs can optionally be a single file.

Multi CLIs are like `git` or `adb`. They have subcommands that are themselves single CLIs. This directory contains all the subcommands for the CLI. For example, the script `command/hello/world` would be available through `$ clif hello world`. Any arguments passed after the command will be curried through to the script, making it trivial to pass values and options around as needed.

The CLI commands are just a stock-standard Node.js, Python, Go, or Bash script with a filename that matches the command name. These scripts are contained within the `command` folder or within nested folders there if you want to create a tree-based command structure.

The simplest way to add a multi-command, however, is to just run `$ clif multi [command name]` and have it lay down the files for you to customise. If, however, you want to create a simple single CLI command, then you can run `$ clif single [command name]`.

### Contextual Help
The CLI provides tools which enable users to easily discover how to use your command line without needing to read your docs. To make this possible, you'll want to add help for each command.

The `[command]/help` file is used to it the arguments that your command accepts, as well as provide a bit of additional context around how it works, when you should use it etc.

In addition to providing help for commands, you may also provide it for directories to explain what their sub-commands are intended to achieve. To do this, simply add a `-h|--help` option to the command file in the directory.

## Updating the CLI
To update the CLI, simply run the command `$ clif update`. More precisely, the update command runs a git pull with the given parameters to merge the retrieved branch heads into the current version of the CLI.

## Autocomplete
Autocomplete functionality will be added soon to make navigating the command line even easier.

## Frequently Asked Questions

1. **Can I use the CLI to run things which aren't bash scripts?**
   Absolutely, the CLI simply executes files - it doesn't care whether they're written in Bash, Node, Python or Go - if you can execute the file then you can use it with the CLI.

2. **Will the CLI work on my Mac?**
   It should, we've built everything to keep it as portable as possible, so if you do have a problem don't hesitate to open a bug report.

3. **Does it allow me to use tab-autocomplete?**
   Not yet. The install command will soon include this.
