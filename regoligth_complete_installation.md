# My Regolith installation

>Note: I prefer to install ubuntun, then install [Regolith Desktop 1.6 PPA](https://regolith-linux.org/download/)

## Update and Upgrade

```bash
sudo apt update && sudo apt upgrade -y
```

## Remove snapcore. It is a trash
```bash
sudo apt remove --purge snapd
```

## Set up visudo without password - optional
* Run the following as **root**

```bash
sudo cat <<EOF > /etc/sudoers.d/10-admins
mflores    ALL=(ALL:ALL) NOPASSWD: ALL
EOF
```
* Return to the normal user
```bash
sudo -k && sudo id
```

## Install vim and set up as default

```bash
sudo apt install vim -y && \
sudo update-alternatives --install /usr/bin/editor editor /usr/bin/vim 10
```
* Select vim as default
```bash
sudo update-alternatives --config editor 
```

## Install regoliht themes
```bash
i=$(apt search  ^regolith-look- | awk -F  "/" '/^regolith-look-/ {print $1}')
for p in $i; do
  sudo apt-get install $p -y
done
```

## Check all availables i3xrocks
* Search and select your favorites
```bash
sudo apt search i3xrocks-
```
* Example installation

```bash
sudo apt install i3xrocks-wifi i3xrocks-time i3xrocks-temp i3xrocks-net-traffic i3xrocks-microphone i3xrocks-memory i3xrocks-disk-capacity i3xrocks-cpu-usage i3xrocks-bluetooth
```

## Install new terminal and zsh shell
```bash
sudo apt install -y terminator tilix zsh git
```

```bash
zsh --version && chsh -s $(which zsh)
```

```bash
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh
```

```bash
mkdir ~/tmp && cd ~/tmp && \
git clone https://github.com/MichaelThessel/tilix-gruvbox.git && \
cd ./tilix-gruvbox && \
sudo cp gruvbox-* /usr/share/tilix/schemes && cd .. && \
rm -rf tilix-gruvbox
```

```bash
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/AnonymousPro.zip && \
mkdir ~/.fonts/ && unzip ./Download/<fontName> -d ~/.fonts/ && \
fc-cache -fv
```

```bash
curl -L https://raw.githubusercontent.com/sbugzu/gruvbox-zsh/master/gruvbox.zsh-theme > ~/.oh-my-zsh/custom/themes/gruvbox.zsh-theme
```

* Modify the **zshrc** file
> ZSH_THEME="gruvbox" 
> SOLARIZED_THEME="dark"

```bash
cp  ~/.zshrc ~./.zshrc.bkp$(date +%y%m%d)
```

```bash
sed -i 's/^ZSH_THEME="robbyrussell"/ZSH_THEME="gruvbox"/g' ~/.zshrc
```

```bash
sed -i '/^ZSH_THEME="gruvbox"/a SOLARIZED_THEME="dark"' ~/.zshrc
```
 
## Modify like the following
```bash
sudo update-alternatives --config x-terminal-emulator # Select terminator
```
## Install zsh for root - optional

```bash
sudo -i
```

```bash
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh 
```

```bash
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc && source ~/.zshrc 
```

```bash
# modify the file
vim ~/.zshrc
# ZSH_THEME="gruvbox" 
# SOLARIZED_THEME="dark"
```
 
## Go to the GUI
* Go to Terminator > Preferences > Profiles > General > uncheck "Use the system fixed width font" > Anonymice Nerd Font Regular > 12
* Go to Terminator > Preferences > Profiles > Colors > Built-in schemes > gruvbox dark
* Go to Terminator > Global > Check "Re-use profiles for new terminals"

## Install i3 layouts

### clone private git
mkdir ./repo; cd ./repo
git clone https://github.com/volcan600/scripts.git

# launch i3 layouts at startup
cp -r ~/repo/scripts/personal.i3_layouts ~
gnome-session-properties
Click on Add > Name: i3_startup > Command: /home/mflores/.i3_layouts/startup_i3_workspaces.sh > Add > Close

# Enable Night Light
Super + c > Displays > Night Light

# Install custom theme
sudo cp -r ./scripts/personal/astro-theme/astro /etc/regolith/styles/
sudo cp -r ./scripts/personal/astro-theme/themes/* /usr/share/themes
sudo cp -r ./scripts/personal/astro-theme/icons/* /usr/share/icons
for f in ~/repo/scripts/personal/astro-theme/icons/*.tar.xz; do tar xf "$f"; done
sudo mv ~/repo/Sweet-{Mars,Purple,Rainbow,Red,Yellow,Nebula} /usr/share/icons/
for f in ~/repo/scripts/personal/astro-theme/themes/*.tar.xz; do tar xf "$f"; done
sudo mv ~/repo/Sweet-{Dark,mars} /usr/share/themes/
mkdir ~/Pictures/FavoriteWallpapers; cp ./scripts/personal/astro-theme/astronaut.jpg ~/Pictures/FavoriteWallpapers

# Install personal packages
slack
sublime
google-chrome
firefox
telegram
anydesk
spotify
vmware
minecraft
steam
zoom
visualstudio
brave
discord
vlc-media
libreoffice
flameshot #enable flameshot in startup
dropbox
teams
wireshark
dbeaver
anaconda
  find anaconda-navigador in cli
  vim ../.local/share/applications/anaconda-navigator.desktop
#!/usr/bin/env xdg-open
[Desktop Entry]
Name=Anaconda
Version=2.0
Type=Application
Exec=/home/mflores/anaconda3/bin/anaconda-navigator
Icon=/home/mflores/anaconda3/lib/python3.8/site-packages/anaconda_navigator/static/images/anaconda-icon-256x256.png
Comment=Open Anaconda Navigator
Terminal=false
minikube
docker
gitkraken

Installation Ubuntu - Marlon 2021
- Sign in on google and microsoft
- update the system
sudo apt update -y && sudo apt upgrade -y
- turn off suspend
- turn on night mode
- display 144hz
- mouse speed top
- remove snap store
sudo apt remove --purge snapd
- install git
sudo apt install git
- add mflores to sudoers without password required
sudo visudo -f /etc/sudoers.d/10-admins
mflores ALL=(ALL) NOPASSWD: ALL
- install google chrome
- login on firefox and google chrome
- install vim and setup as default
sudo apt install vim -y
sudo update-alternatives --config editor
- create a directory where all repo will store
mkdir ~/repo
git clone private repo
store git hub creentials
- install sublim using repo
