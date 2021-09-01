# New laptop installs

## What I installed on a new Ubuntu 20 laptop

### Softwares

- VSCode (from Ubuntu Software)
- WebStorm (from Ubuntu Software)

    In settings icon of the project files hierarchy : check "open files with a single click" and "always select opened files)

- [Terminator](https://unix.stackexchange.com/questions/168436/how-to-open-terminal-split-to-9-terminals-and-switch-between-them-using-one-scr) (from Ubuntu Software)
    1. Install from Ubuntu Software
    2. Open terminator and split the window in 3
    3. Right click > Preferences > Layout > Add
    4. That will populate the Layouts list with your new layout
    5. Find each of the terminals you have created in the layout and click on them. Then on the right, enter the command you want to run in them on startup, for example `cd ~/dev ; bash`. ⚠️ Note that the command is followed by `; bash`. If you don't do that, the terminals will not be accessible, since they will run the command you give and exit.
    6. Once you have set all the commands, click Close and then exit terminator.
    7. Open the terminator config file `~/.config/terminator/config` and delete the section under layouts for the default config. Then change the name of the layout you created to default.
    8. [with commands and title](https://bytefreaks.net/gnulinux/bash/custom-terminator-layout-with-multiple-tabs-and-terminals)

    ```bash
    [global_config]
      window_state = maximise
      title_transmit_bg_color = "#ad7fa8"
      suppress_multiple_term_dialog = True
    [keybindings]
    [profiles]
      [[default]]
        cursor_color = "#aaaaaa"
    [layouts]
      [[default]]
        [[[child0]]]
          type = Window
          parent = ""
          order = 0
          position = 72:27
          maximised = True
          fullscreen = False
          size = 1848, 1016
          title = maty@maty-HP-ProBook-650-G4: ~
          last_active_term = 63008736-7bc6-49c1-a7a7-15e2adae602f
          last_active_window = True
        [[[child1]]]
          type = HPaned
          parent = child0
          order = 0
          position = 924
          ratio = 0.5013564839934889
        [[[terminal2]]]
          type = Terminal
          parent = child1
          order = 0
          profile = default
          title = React sources
          uuid = 63008736-7bc6-49c1-a7a7-15e2adae602f
          directory = ~/dev
        [[[child3]]]
          type = VPaned
          parent = child1
          order = 1
          position = 508
          ratio = 0.5024727992087042
        [[[terminal4]]]
          type = Terminal
          parent = child3
          order = 0
          profile = default
          uuid = f074e9ad-596b-4d94-8b1b-7fb0c66f829d
        [[[terminal5]]]
          type = Terminal
          parent = child3
          order = 1
          profile = default
          uuid = d7a0be0c-cdf3-49c9-838b-c7a18f09e77f
    [plugins]
    ```

- Zsh
    1. Install zsh and make it default

        ```bash
        sudo apt-get install zsh

        chsh -s $(which zsh)
        ```

    2. Restart your terminal. You should see the configuration menu of zsh and choose option 2: Populate your ~/.zshrc with the configuration recommended by the system administrator and exit
    3. Move your configuration and aliases from .bashrc to .zshrc (copy "export" sections)
    4. Install Oh My Zsh

        ```bash
        sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

        sudo apt-get install fonts-powerline

        # Install autosuggestions plugin
        git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
        ```

    5. Change ZSH_THEME="robbyrussell" to ZSH_THEME="agnoster" in your .zshrc
    6. Add the plugin to the list of plugins for Oh My Zsh to load (inside ~/.zshrc): plugins=(zsh-autosuggestions)
    7. Install syntax highlighting

        ```bash
        git clone https://github.com/zsh-users/zsh-syntax-highlighting.git

        echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
        ```

    8. 
    9. Restart your terminal
- Google Chrome
- Peek (from Ubuntu Software)

### Packages

- cURL

    ```bash
    sudo apt  install curl
    ```

- Git

    ```bash
    sudo apt-get install git

    git config --global user.email "you@example.com"

    git config --global user.name "Your Name"
    ```

- [NVM](https://github.com/nvm-sh/nvm)

    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash

    export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm

    ```

- Node.js

    ```bash
    nvm install node
    ```

- Yarn

    ```bash
    npm install --global yarn
    ```

- ADB

    ```bash
    sudo apt-get install android-tools-adb
    ```

- React DevTools

    ```bash
    npm i -g react-devtools

    # launch devtools
    adb reverse tcp:8097 tcp:8097
    react-devtools
    ```

- Expo

    ```bash
    npm install --global expo-cli
    ```

### Online resources

- Figma
- [Shell commands](https://aiko.dev/shell-commands/)

### Expo project with TypeScript

- [Tutorial with ESLint and Prettier](https://justinnoel.dev/2020/07/20/enforcing-consistent-and-error-free-code-in-an-expo-react-native-project-with-typescript/)
- [Bottom navigation bar](https://reactnavigation.org/blog/2020/01/29/using-react-navigation-5-with-react-native-paper/)
- Build APK

    ```bash
    npm i -g react-native
    ```

    ```bash
    react-native bundle --platform android --dev false --entry-file node_modules/expo/AppEntry.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
    ```

```bash
cd android

```

### Shortcuts

- WebStorm
    1. Double shift and select "Live templates"
    2. In "JavaScript" section, click plus to add a new template
    3. Name it "cl", choose context and type :

        ```bash
        console.log("[$FUNCTION$], 👋 $PARAM_TEXT$: ", $PARAM$)$END$
        ```

    4. Click "edit variables" and enter "‘jsMethodName()" for FUNCTION
    5. Add ‘PARAM’ as a default Value of PARAM_TEXT
    6. Check "skip if defined" for PARAM_TEXT and FUNCTION
    7. Order variables so that PARAM comes before PARAM_TEXT
    8. Same thing with "cw" and emoji 🔥, "cd" and "console.warn" + emoji 👿, "cll" and remove PARAMS
