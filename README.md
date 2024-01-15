# Terminal Cowsay Script

Welcome to the Terminal Cowsay Script repository! This simple script adds a touch of fun to your terminal experience by displaying a whimsical greeting in the form of a speech bubble from a .cow file every time you open the terminal.

## Features

- Displays an entertaining cowsay greeting upon each terminal opening.

## Usage

1. **Clone the repository:**
    ```bash
    git clone https://github.com/IlYAN-FISHERMAN/Cowsay_scrypt.git
    ```

2. **Move the `.cowsay` folder to the same location as your `.zshrc` file.**

3. **Add the following script to your `.zshrc` file:**
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
4. **Source your `.zshrc` file:**
    ```bash
    source .zshrc
    ```

Now, each time you open your terminal, you'll be greeted with a delightful cowsay message!

## Prerequisites

Ensure you have `cowsay` and `fortune` installed:
```bash
brew install cowsay && brew install fortune
