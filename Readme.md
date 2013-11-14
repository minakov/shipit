# shipit :shipit:

Minimalistic SSH deployment.


## Installation

  $ path=/usr/local/bin/shipit; curl -o $path https://raw.github.com/sapegin/shipit/master/bin/shipit; chmod +x $path; unset path

You can use this command to update shipit too.


## Usage

  shipit [command|option]

### Options

| -V, --version   | Print program version |
| -h, --help      | Print help (this screen) |

### Commands

| <target>        | Executes <target> target on remote host (run shipit to execute 'deploy' target) |
| list            | Print list of available targets |
| console         | Open an SSH session on remote host |
| exec <cmd>      | Execute <cmd> on remote host |

### Examples

  $ shipit

  Will execute `deploy` target.

  $ shipit status

  Will execute `status` target.

  $ shipit list

  Will show a list of available targets.

  $ shipit exec uptime

  Will execute `uptime` command on remote host.


## Configuration

You need to create `.shipit` file in your project’s directory.

Here is a typical config:

  host='myhost'
  path='sites/example.com'

  [deploy]
  git checkout master
  git pull
  npm install
  node -e "require('grunt').cli()" _ deploy
  
  [status]
  uptime

The only required things is `host` and `path` parameters and `[deploy]` target.

### Parameters

### host

It’s the same host you use in `ssh` command. It could be string of format `<username>@<ip>:<port>` or just a name of `~/.ssh/config` record.

### path

Project path on remote host. shipit will `cd` to this directory before executing any command.

### Targets

Target is just a bunch of shell command that will be executed on remote host via SSH. You can define as many targets as you want.


## Changelog

The changelog can be found in the `Changelog.md` file.


---

## License

The MIT License, see the included `License.md` file.