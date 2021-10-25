# Setup

### ConEmu (optional for windows)
ConEmu is a console emulated for running shell scripts in terminal. Install instructions here: https://conemu.github.io/

### oh-my-zsh 
Oh-my-zsh is an open source framework for programming functions, helpers, plugins, themes in terminal instead of Unix/Bash commands to execute a shell script.

#### In terminal, run the following command lines seperately. `sh-c` installs oh-my-zsh from github repo
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    exec $SHELL -l
            git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOMpluginszsh-syntax-highlighting
    git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
    git clone https://github.com/paulirish/git-open.git $ZSH_CUSTOM/plugins/git-open
    git clone https://github.com/powerline/fonts.git --depth=1
    cd fonts
    ./install.sh
    cd ..
    rm -rf fonts    

#### Set up .zshrc file with plugins and alias that can be usd in terminal command line
Any `.` file will be stored locally, but hidden from the repo. For setting up this file, see the example script I saved here for you here.    

#### Give your user permissions and set default shell to zsh
    sudo chmod 775 '.zshrc' 
    chsh -s /bin/zsh

## Python 3
#### Download recent stable package of Python (although 3.7 was configured with this setup)
    brew install pyenv
    pyenv install 3.7.12
    ls ~/.pyenv/versions/
    pyenv global 3.7.12

#### Add if python is store locally but with different path to .zshrc
    if command -v pyenv 1>/dev/null 2>&1; then
        export PATH=$(pyenv root)/shims:$PATH
    fi 
## Pip
#### Download pip and install
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
    python get-pip.py

## Git  
#### Install and configure Git user with email (optional)
    git --version
    git config --global user.name "<ad-im-uk>"
    git config --global user.email "<adrian.imbrea91@yahoo.com>"

### Clone github respository 
#### Store the repo to local drive to align with parent Github directory
    git clone git@github.com:ramseywise/First-Flask-App.git

### Configure Git for SSH access (optional for sharing repo)
Add personal access token under `/<github_user_profile>/settings/developer settings/` (be sure to save this!)

#### Open ssh folder and generate ssh key for private and public file
    ssh-keygen -t ed25519
    cd ~/.ssh
    ls

#### Start SSH agent
    eval "$(ssh-agent -s)"

#### Add `~/.ssh/config`  folder with the following contents (keys are optional)
        Host github.com
        AddKeysToAgent yes
        UseKeychain yes
        IdentityFile ~/.ssh/<private_ssh_key_file>

#### Add private ssh key file to keychain
    ssh-add -K ~/.ssh/id_ed25519

#### Add public key (id_ed26619) to github 
Navigate to `/<github_user_profile>/settings/SSH and GPG keys/`

## Docker   
Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications, whether on laptops, data center VMs, or the cloud. Simply put, this allows us to build and run code within isolated containers on the cloud, so you can develop features that will later be deployed to the N26 app. 
#### Install docker
    curl -L https://github.com/docker/machine/releases/download/v0.16.1/docker-machine-`uname -s`-`uname -m` >/usr/local/bin/docker-machine
#### Give user permissions
    chmod +x /usr/local/bin/docker-machine
#### Login using artifactory (optional)
    docker login artifactory.cd-tech26.de
    docker pull artifactory.cd-tech26.de/docker/n26/python3.7.2-slim:latest

## AWS Client (optional)
#### Install AWS Client
    brew install awscli
#### Create the file ~/.aws/credentials with the following contents
        [default]
        aws_access_key_id = foo
        aws_secret_access_key = foo
#### Create the file ~/.aws/config with the following contents
        [default]
        region = eu-central-1

## Visual Studio Code (optional)
#### Install Vscode 
#### Set path to open in terminal with command alias `code`
#### Open VScode command pallet (CMD + Shift + P)
Type `shell` to select `Shell Command: install 'code' command in PATH

#### Add extensions
- `Atom` keyboard for shortcuts
- `Python` for debugging
- `Pylance` for additional python support
- `Python Indent` for automatic tabs
- `Black` for linting format
- `Prettier` for code formatting
- `IntelliCode` for auto completion
- `GitLens` for Git support
- `Jupyter` for notebook support in VScode
- `Docker` for maintaining applications extensions 
- `Beautify` for javascript, JSON, CSS, HTML

For more web development extensions, see https://codeforgeek.combest-visual-studio-code-extensions-web-development/ 
