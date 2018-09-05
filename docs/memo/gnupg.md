# GnuPG

## Install

Linux (Fedora)

```
dnf install pinentry-gtk
```

macOS

```
brew install gnupg pinentry-mac
```

## Configurations

`~/.gnupg/gpg-agent.conf`

Linux

```
default-cache-ttl 43200
max-cache-ttl 43200
pinentry-program /usr/bin/pinentry-gtk-2
```

macOS

```
pinentry-program /usr/local/bin/pinentry-mac
```
