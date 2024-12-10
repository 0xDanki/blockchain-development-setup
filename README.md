# Blockchain Development Local Setup Guide

If you're new to blockchain development and need to start from scratch, this guide will walk you through setting up a blockchain development environment using WSL2, Hyper, Zsh, OhMyZsh, VSCode, and more.

## Table of Contents

1. [Enable WSL2](#1-enable-wsl2)
2. [Install a Linux Distribution for WSL2](#2-install-a-linux-distribution-for-wsl2)
3. [Install Chocolatey](#3-install-chocolatey)
4. [Install Hyper and VS Code](#4-install-hyper-and-vs-code)
5. [Set Hyper to use WSL](#5-set-hyper-to-use-wsl)
6. [Install Zsh and Oh My Zsh](#6-install-zsh-and-oh-my-zsh)
7. [Install NVM using Zsh](#7-install-nvm-using-zsh)
8. [Install Node.js using NVM](#8-install-nodejs-using-nvm)
9. [Install Yarn](#9-install-yarn)
10. [Install Global NPM Packages](#10-install-global-npm-packages)
11. [Install Neofetch](#11-install-neofetch)
12. [Install VS Code Extensions](#12-install-vs-code-extensions)
13. [Install Powerlevel9k Theme for Oh My Zsh](#13-install-powerlevel9k-theme-for-oh-my-zsh)
14. [Install Powerline Fonts](#14-install-powerline-fonts)
15. [Configure Hyper Font](#15-configure-hyper-font)
16. [Setup Powerlevel9k](#16-setup-powerlevel9k)
17. [Install Hyper Plugins](#17-install-hyper-plugins)
18. [Upgrade Ubuntu](#18-upgrade-ubuntu)
19. [Install Zsh Plugins](#19-install-zsh-plugins)
20. [Configure VS Code Integrated Terminal Font](#20-configure-vs-code-integrated-terminal-font)
21. [Install MetaMask](#21-install-metamask)
22. [Create a Developer Wallet in MetaMask](#22-create-a-developer-wallet-in-metamask)
23. [Connect to Sepolia Testnet](#23-connect-to-sepolia-testnet)
24. [Obtain Sepolia Testnet Tokens](#24-obtain-sepolia-testnet-tokens)

## 1. Enable WSL2

Run in PowerShell as administrator:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
```

## 2. Install a Linux Distribution for WSL2

1. Open Microsoft Store on Windows.
2. Search for "Linux".
3. Install Ubuntu.

## 3. Install Chocolatey

Run the following command in CMD as administrator:

```cmd
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

## 4. Install Hyper and VS Code

Run in CMD as administrator:

```cmd
choco install hyper vscode -y
```

## 5. Set Hyper to use WSL

1. Right-click Hyper icon > Properties > Compatibility > check "Run as administrator".
2. Open Hyper.
3. Go to Edit > Preferences.
4. A window with 'hyper.js' filename will open. Find the shell settings and change these lines:
   ```
   shell: 'C:\\Windows\\System32\\wsl.exe',
   shellArgs: ['~'],
   ```
5. Save preferences and restart Hyper.

## 6. Install Zsh and OhMyZsh

Run in Hyper:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install zsh -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## 7. Install NVM using Zsh

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.0/install.sh | bash
echo "export NVM_DIR=\"$HOME/.nvm\"\n[ -s \"$NVM_DIR/nvm.sh\" ] && \. \"$NVM_DIR/nvm.sh\"\n[ -s \"$NVM_DIR/bash_completion\" ] && \. \"$NVM_DIR/bash_completion\"" >> ~/.zshrc
source ~/.zshrc
```

## 8. Install Node.js using NVM

```bash
nvm install node
nvm alias default node
```

## 9. Install Yarn

```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install --no-install-recommends yarn
```

## 10. Install Global NPM Packages

```bash
npm i -g nodemon pm2 eslint pug
```

## 11. Install Neofetch

```bash
sudo apt install neofetch
echo 'neofetch' >> ~/.zshrc
```

## 12. Install VS Code Extensions

Open VSCode and click on the extensions icon.

Search and install the following extensions:
- Remote - WSL
- Solidity
- Ethereum Remix
- Git Graph
- GitLens
- Prettier
- Tailwind (To those who use TailwindCSS for frontend)

## 13. Install Powerlevel9k Theme for Oh My Zsh

```bash
git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
```

Then, add to your ~/.zshrc:

```
ZSH_THEME="powerlevel9k/powerlevel9k"
```

## 14. Install Powerline Fonts

For Windows, download and install manually from: [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts/releases)

Or, for Powerline Fonts, run in PowerShell:

```powershell
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts
Set-ExecutionPolicy Bypass
./install.ps1
cd ..
Remove-Item fonts -Recurse -Force
```

Recommended fonts: FuraMono, FiraCode, Menlo, DejaVu Sans, Hack, HeavyData

## 15. Configure Hyper Font

In Hyper preferences, set:

```
fontFamily: '"FuraMono Nerd Font Mono", "FuraMono Nerd Font", Menlo, "DejaVu Sans Mono", Consolas, "Lucida Console", monospace'
```

## 16. Setup Powerlevel9k

Add to your ~/.zshrc:

```
POWERLEVEL9K_MODE='nerdfont-complete'
```

## 17. Install Hyper Plugins

```
hyper i hyper-statusline hyper-search hyper-oceanic-next
```

## 18. Upgrade Ubuntu

```bash
sudo apt upgrade -y
```

## 19. Install Zsh Plugins

```bash
# zsh-completions
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:=~/.oh-my-zsh/custom}/plugins/zsh-completions
# zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
# fasd
sudo apt install fasd -y
```

Edit ~/.zshrc and add these plugins:

```
plugins=(
    ansible
    aws
    cargo
    command-not-found
    docker
    fasd
    git
    golang
    npm
    npx
    nvm
    react-native
    rust
    sudo
    systemd
    ubuntu
    vscode
    web-search
    yarn
    zsh-autosuggestions
    zsh-completions
)
```

## 20. Configure VS Code Integrated Terminal Fon

In VS Code settings, add:

```json
"terminal.integrated.fontFamily": "'FuraMono Nerd Font Mono'",
"terminal.integrated.fontSize": 12
```

## 21. Install MetaMask

1. Go to the [MetaMask website](https://metamask.io/download/).
2. Click "Install MetaMask for [Your Browser]".
3. Follow the installation prompts.

## 22. Create a Developer Wallet in MetaMask

1. Click on the MetaMask extension icon in your browser toolbar.
2. If you're new to MetaMask, follow the setup process to create your first wallet.
3. If you already have a wallet, click on the account icon in the top-right corner.
4. Select "Create Account" or "Add Account" from the dropdown menu.
5. Name this new account "Developer Wallet" or something similar to easily distinguish it.
6. Click "Create" to finalize the new wallet creation.

⚠️ **WARNING**: This developer wallet should be kept separate from your personal wallet. Do not use it for storing any valuable amount of tokens or cryptocurrencies. It's intended solely for development and testing purposes and may be more vulnerable to security risks during the development process.

## 23. Connect to Sepolia Testnet

1. In MetaMask, click the network dropdown.
2. Select "Add network" > "Add a network manually".
3. Fill in the Sepolia testnet details:
   - Network Name: Sepolia Test Network
   - New RPC URL: https://rpc.sepolia.org
   - Chain ID: 11155111
   - Currency Symbol: ETH
   - Block Explorer URL: https://sepolia.etherscan.io

## 24. Obtain Sepolia Testnet Tokens

1. Go to the [Sepolia Faucet](https://sepoliafaucet.com/).
2. Connect your MetaMask wallet and request testnet ETH.

## 25. Install Foundry

Foundry is a blazing fast, portable and modular toolkit for Ethereum application development written in Rust. It consists of three main tools:

- `forge`: Ethereum testing framework (like Truffle, Hardhat, and DappTools).
- `cast`: Swiss army knife for interacting with EVM smart contracts, sending transactions, and getting chain data.
- `anvil`: Local Ethereum node, akin to Ganache, Hardhat Network, or DappTools' `ethers-geth`.

### Installation Steps

1. Open your terminal (make sure you're in your WSL environment).

2. Install Foundry using the official installer:
   ```bash
   curl -L https://foundry.paradigm.xyz | bash

Congratulations! You now have a blockchain development environment set up and essential development tools. You're ready to start developing decentralized applications and tools in Ethereum from your local machine!

## What comes after: Setting Up Your Blockchain Project

### Creating a new project with Foundry

If you have Foundry installed, let's set up a new project:

```bash
mkdir folder_name
cd folder_name
```

To start a new project with Foundry, use the `forge init` command:

```bash
forge init folder_name
```

### Creating a new project with Hardhat

Hardhat is a popular development environment for Ethereum software. It's designed to help you manage and automate the recurring tasks inherent to developing smart contracts and dApps. Here's how to set up a new project with Hardhat:

```bash
mkdir folder_name
cd folder_name
```

Then initialize an npm project as shown below. You'll be prompted to answer some questions.

```bash
npm init
```

Now we install Hardhat:

```bash
npm install --save-dev hardhat
```

Now, we initialize Hardhat on the project:

```bash
npx hardhat init
```

```
👷 Welcome to Hardhat v2.22.17 👷‍

? What do you want to do? …
  Create a JavaScript project
  Create a TypeScript project
  Create a TypeScript project (with Viem)
❯ Create an empty hardhat.config.js
  Quit
```

Finally, answer the setup questions about the project you are creating. You are now ready to write your contracts!

