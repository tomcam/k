# Installing Kore on MacOS/OSX

Here's how to install Kore on MacOS using Homebrew.

## Installing Homebrew

[Homebrew](https://brew.sh/) is a [package manager](https://en.wikipedia.org/wiki/Package_manager) for MacOS. Package managers keep track of all the files needed for an app (or a library such as Kore). If you don't already have Homebrew, here's how to install it.

* Hold down the `⌘` (Command key) and the space key at the same time to open up Spotlight.

* Type the world `terminal` and press Enter.

The MacOS Terminal appears.

* Copy and paste the following command, then press Enter. Leave in the quotes.

```text
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

* Once Homebrew has been installed, issue this command in Terminal:

```text
brew install kore
```
