# Basic Dependencies
sudo pacman -S tar tree multitail tldr trash-cli unzip fastfetch cmake make neovim git freetype2 fontconfig pkg-config make libxcb libxkbcommon python

# Install Paru Aur Helper
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si

# Nerd Fonts
git clone https://github.com/ryanoasis/nerd-fonts.git
./install.sh

# Setup lazyvim from scratch

# Setup Alacritty
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup override set stable
rustup update stable
git clone https://github.com/alacritty/alacritty.git
cd alacritty
cargo build --release
sudo cp target/release/alacritty /usr/local/bin # or anywhere else in $PATH
sudo cp extra/logo/alacritty-term.svg /usr/share/pixmaps/Alacritty.svg
sudo desktop-file-install extra/linux/Alacritty.desktop
sudo update-desktop-database
mkdir -p ~/.bash_completion
cp extra/completions/alacritty.bash ~/.bash_completion/alacritty
echo "source ~/.bash_completion/alacritty" >> ~/.bashrc

# Setup Lutris
sudo pacman -S lutris

# Setup Wine Dependencies
sudo pacman -S --needed wine-staging giflib lib32-giflib libpng lib32-libpng libldap lib32-libldap gnutls lib32-gnutls \
mpg123 lib32-mpg123 openal lib32-openal v4l-utils lib32-v4l-utils libpulse lib32-libpulse libgpg-error \
lib32-libgpg-error alsa-plugins lib32-alsa-plugins alsa-lib lib32-alsa-lib libjpeg-turbo lib32-libjpeg-turbo \
sqlite lib32-sqlite libxcomposite lib32-libxcomposite libxinerama lib32-libgcrypt libgcrypt lib32-libxinerama \
ncurses lib32-ncurses ocl-icd lib32-ocl-icd libxslt lib32-libxslt libva lib32-libva gtk3 \
lib32-gtk3 gst-plugins-base-libs lib32-gst-plugins-base-libs vulkan-icd-loader lib32-vulkan-icd-loader

# Setup Steam
sudo pacman -S steam

# Setup Flatpak
sudo pacman -S flatpak

# Setup Bottles
flatpak install flathub com.usebottles.bottles

# Setup Nix package manager
sudo sh <(curl -L https://nixos.org/nix/install) --daemon

# Setup DWM
cd
mkdir Github
git clone https://git.suckless.org/dwm