# Bash

## What and Why of scripting with Bash

### The operating system being used

```sh
$ lsb_release -a
```

```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:        22.04
Codename:       jammy
```

### The bash version

```sh
echo $BASH_VERSION
```

```
5.1.16(1)-release
```

### Check the vulnerability of the code

```sh
$ env 'x=() { :;}; echo vulnerable''BASH_FUNC_x()=() { :;}; echo vulnerable' bash -c "echo test"
```

Then, the expected output is test

```
test
```

This is again to check the vulnerability

```sh
$ cd /tmp; rm -f /tmp/echo; env 'x=() { (a)=>\' bash -c "echo date"; cat /tmp/echo
```

And then expected output should be the following

```
date
cat: /tmp/echo: No such file or directory
```

### See what the `type` of command is

#### type

Use `type` to know the types of commands.

- Alias
- Function
- Shell built in
- Keyword
- File

Example, `type ls` outputs

```sh
$ type ls
```

```
ls is aliased to `ls --color=auto'
```

#### type -a

We can extend this further to display all the matches for the given command:

```bash
$ type -a ls
```

```
ls is aliased to `ls --color=auto'
ls is /usr/bin/ls
ls is /bin/ls
```

#### type -t

If you simply want to know the type of the command, use `-t`

```bash
$ type -t ls
```

```
alias
```
