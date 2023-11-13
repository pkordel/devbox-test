# How to setup and use devbox

## What is devbox?

Devbox allows developers to manage system level services, isolated to specific projects.
Imagine managing specific versions of postgres, nats or redis without having to incur the overhead of virtualization e.g. Docker.

See https://www.jetpack.io/devbox/docs/ for more, including installation.

## Getting started

- Normally, you would run `devbox init` in your project directory to create a starter `devbox.json` file
- This repository already includes a sample file you can use to experiment

Once devbox is installed, you simple run `devbox shell` to start a devbox session. 
This may take a little while the very first time but is quick the next time you run it.
Installed packages are managed just like system services or brew services.

Let's see what services are installed: 
- open a new terminal and cd into this directory
- start your session via `devbox shell`
- `devbox services ls` to list your services
- `devbox services up` to start them

You will get complaints from postgresql, let's fix that.
- in the original terminal, run:
```
devbox shell
initdb
createdb `whoami`
```

To stop your services, in the original shell type `devbox services down` or in the services terminal, use F10.

## Using direnv

Check out this guide for direnv integration if you like: https://www.jetpack.io/devbox/docs/ide_configuration/direnv/. 
There are several ways to install direnv, feel free to use the one you like best. 
I use `asdf` as a version manager with the direnv plugin, but you can use e.g. `brew` as well.

## Missing a package?

You can search for available packages with devbox. E.g. `devbox search mongodb` and then `devbox add mongodb` (if you omit the version, it defaults to the latest version)
