#! /usr/bin/env bash


defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool true
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true
# sudo nvram SystemAudioVolume=" "
sudo nvram SystemAudioVolume=%80

# Prevent Gatekeeper Turning Back On Automatically in OS X
# http://osxdaily.com/2015/11/05/stop-gatekeeper-auto-rearm-mac-os-x/
sudo defaults write /Library/Preferences/com.apple.security GKAutoRearm -bool NO


# I'd suggest running this script under a different acconnt to your normal account. Otherwise
# TimeMachine will will assume you own the brew install and will restore it when you use the
# Data Migration tool

# Install Apple CLI Dev tools, java and my preferred homebrew and cask software

#Xcode cli now installed by homebrew I'm told
#xcode-select --install # Works on Mavericks and hopfully above

echo
read -p "Please wait until CLI tools are installed and press enter"  < /dev/tty

ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

#Symlink into the normal place. Add this to login scripts as well
export HOMEBREW_CASK_OPTS="--appdir=/Applications"

brew tap caskroom/cask
brew tap caskroom/versions

brew install brew-cask

brew cask install java
brew cask install xquartz #Pre-req for some of the brew packages

brew install python --framework
brew linkapps python
brew install putty --with-gtk+

brew install ack
brew install bfg
cd $(brew --prefix)/bin
ln -s bfg git-bfg
brew install byacc
brew install cabextract
brew install cmake
brew install coreutils
brew install direnv
brew install findutils
brew install flex
brew install gawk
brew install gcc
brew install git
brew install gnu-sed
brew install go
brew install ispell
brew install jdiskreport
brew install kdiff3
brew install lua52
brew install minicom
brew install macvim
brew unlink macvim
brew cleanup
brew link macvim

[[ -L /Applications/MacVim.app ]] && sudo rm -rf /Applications/MacVim.app
sudo -u admin ln -s /usr/local/Cellar/macvim/*/MacVim.app /Applications/MacVim.app

brew install multimarkdown
brew install mutt
brew install node
brew install offline-imap
brew install p7zip
brew install pandoc
brew install sqlite
brew install ssh-copy-id
brew install svn
brew install the_silver_searcher
brew install tmux
brew install wget
brew install wine
brew install winetricks
brew install z

brew cask install adium
brew cask install adobe-air
brew cask install anki
brew cask install arduino
brew cask install atom
brew cask install bartender
brew cask install caffeine
brew cask install calibre
brew cask install chicken
brew cask install controlplane
brew cask install dash
brew cask install dropbox
brew cask install eclipse-ide
brew cask install evernote
brew cask install filezilla
brew cask install flash
brew cask install flip4mac
brew cask install flux
brew cask install freeplane
brew cask install fritzing
brew cask install gimp
brew cask install gnucash
brew cask install google-chrome
brew cask install google-drive
brew cask install gpgtools
brew cask install iterm2
brew cask install itsycal
brew cask install jdiskreport
brew cask install kdiff3
brew cask install keepassx0
brew cask install libreoffice
brew cask install mactex
# brew cask install macvim # Don't install this. It breaks
brew cask install minecraft
brew cask install music-manager
brew cask install openscad
brew cask install paintbrush
brew cask install quicksilver
brew cask install second-life-viewer
brew cask install sketchup
brew cask install skype
brew cask install slic3r
brew cask install smcfancontrol
brew cask install sourcetree
brew cask install steam
brew cask install stellarium
brew cask install the-unarchiver
brew cask install thunderbird
brew cask install transmission
brew cask install truecrypt71a
brew cask install unrarx
brew cask install vagrant
brew cask install virtualbox
brew cask install vlc
# brew cask install vmware-fusion

brew cleanup
brew cask cleanup

# Install Perlbrew

sudo cpan App::perlbrew
perlbrew init
source $HOME/perl5/perlbrew/etc/bashrc
perlbrew install perl-stable
perlbrew install-cpanm
cpanm --local-lib=~/perl5 local::lib && eval $(perl -I ~/perl5/lib/perl5/ -Mlocal::lib)
# cpanm install CPAN::Mini
# minicpan -l ~/perl5/minicpan -r http://mirror.internode.on.net/pub/cpan/


# Install keybase client (keybase.io)

npm install -g keybase-installer


# Support for Golang

sudo -u admin GOPATH=/tmp GOBIN=/usr/local/opt/go/bin  go get golang.org/x/tools/cmd/...
sudo -u admin GOPATH=/tmp GOBIN=/usr/local/opt/go/bin vim -c ":GoInstallBinaries" /tmp/src/fred.go

