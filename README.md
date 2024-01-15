# Terminal Cowsay Script

## Description

Ce script simple sert à afficher un message de bienvenue sous forme de bulle de pensée d'un fichier .cow à chaque ouverture du terminal.

## Fonctionnalités

- Affiche une salutation amusante avec un cowsay à chaque ouverture du terminal.

## Code
```bash
#!/bin/bash

COWPATH="$COWPATH:$HOME/.cowsay/cowfiles/"

# Cow-spoken fortunes every time you open a terminal
function cowsayfortune
{
    NUMOFCOWS=`cowsay -l | tail -n +2 | wc -w`
    WHICHCOW=$((RANDOM%$NUMOFCOWS+1))
    THISCOW=`cowsay -l | tail -n +2 | sed -e 's/\ /\'$'\n/g' | sed $WHICHCOW'q;d'`

    #echo "Selected cow: ${THISCOW}, from ${WHICHCOW}"
    fortune | cowsay -f $THISCOW -W 100
}

cowsayfortune
```
## Prérequis
```bash
brew install cowsay && brew install fortune
```
## Clone le repos
```bash
git clone https://github.com/IlYAN-FISHERMAN/Cowsay_scrypt.git
```
## Installation
- Clonez le repos
- Mettez le dossier .cowsay au meme endroit que votre .zshrc
- Mettez le script dans votre .zshrc
- Pour finir :
```bash
source .zshrc
```
