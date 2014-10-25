# Add `~/bin` to the `$PATH`
export PATH="$HOME/bin:$PATH";

# Load the shell dotfiles, and then some:
# * ~/.path can be used to extend `$PATH`.
# * ~/.extra can be used for other settings you don’t want to commit.
for file in ~/.{path,bash_prompt,exports,aliases,functions,extra}; do
	[ -r "$file" ] && [ -f "$file" ] && source "$file";
done;
unset file;

# Case-insensitive globbing (used in pathname expansion)
shopt -s nocaseglob;

# Append to the Bash history file, rather than overwriting it
shopt -s histappend;

# Autocorrect typos in path names when using `cd`
shopt -s cdspell;

# Enable some Bash 4 features when possible:
# * `autocd`, e.g. `**/qux` will enter `./foo/bar/baz/qux`
# * Recursive globbing, e.g. `echo **/*.txt`
for option in autocd globstar; do
	shopt -s "$option" 2> /dev/null;
done;

# Add tab completion for many Bash commands
if which brew > /dev/null && [ -f "$(brew --prefix)/etc/bash_completion" ]; then
	source "$(brew --prefix)/etc/bash_completion";
elif [ -f /etc/bash_completion ]; then
	source /etc/bash_completion;
fi;

# Enable tab completion for `g` by marking it as an alias for `git`
if type _git &> /dev/null && [ -f /usr/local/etc/bash_completion.d/git-completion.bash ]; then
	complete -o default -o nospace -F _git g;
fi;

# Add tab completion for SSH hostnames based on ~/.ssh/config, ignoring wildcards
[ -e "$HOME/.ssh/config" ] && complete -o "default" -o "nospace" -W "$(grep "^Host" ~/.ssh/config | grep -v "[?*]" | cut -d " " -f2 | tr ' ' '\n')" scp sftp ssh;

# Add tab completion for `defaults read|write NSGlobalDomain`
# You could just use `-g` instead, but I like being explicit
complete -W "NSGlobalDomain" defaults;

# Add `killall` tab completion for common apps
complete -o "nospace" -W "Contacts Calendar Dock Finder Mail Safari iTunes SystemUIServer Terminal Twitter" killall; 

export ANDROID_HOME=/Users/david/Dropbox/sync/Business/MindfulSound/Development/AndroidDevelopment-20131030/sdk/
export PATH=$PATH:$ANDROID_HOME/tools                  
export PATH=$PATH:$ANDROID_HOME/platform-tools 

alias adb=/Users/david/Development/AndroidSDK/sdk/platform-tools/adb

#use existing ssh-agent if possible
if [ -f ${HOME}/.ssh-agent ]; then
   . ${HOME}/.ssh-agent > /dev/null
fi
if [ -z "$SSH_AGENT_PID" -o -z "`/bin/ps -a|/usr/bin/egrep \"^[ ]+$SSH_AGENT
_PID\"`" ]; then
   /usr/bin/ssh-agent > ${HOME}/.ssh-agent
   . ${HOME}/.ssh-agent > /dev/null
fi

alias findtext='find . -exec egrep '\!*' {} /dev/null \;'
alias battery='ioreg -l | grep -i IOBatteryInfo'

# text editing
alias sub='open -a Sublime\ Text\ 2.app'
alias e='open -a TextMate.app'



