# Ansible OhMyZsh

An Ansible role for installing and configuring <a href="https://ohmyz.sh/" target="_blank">OhMyZsh</a>.

## Variables

All variables are optional unless otherwise specified:

```yaml
ohmyzsh:                                      Array of OhMyZsh configurations per user
  - user: [string]                            [required] The user who's configuration this is 
    updates:                                  Defines the update configuration for this user's installation.
      mode: [auto, reminder, disabled]        Sets OhMyZsh update mode. See https://github.com/ohmyzsh/ohmyzsh/wiki/Settings#update-settings.
      frequency: [integer]                    The frequency of updates. See https://github.com/ohmyzsh/ohmyzsh/wiki/Settings#update-settings for more.
      verbosity: [default, minimal, silent]   The verbosity of update notifications. See https://github.com/ohmyzsh/ohmyzsh/wiki/Settings#update-settings for more.
    plugins:                                  An array of plugins to install for this user.
      - name: [string]                        [required] The name of the plugin
        repository: [string]                  The git repository for the plugin, if it is not builtin.
        version: [string]                     The tag or branch to use. Defaults to HEAD.
    theme:                                    The theme to install for this user.
      name: [string]                          [required] The name of the theme.
      repository: [string]                    The git repository of the theme, if it is not builtin.
      version: [string]                       The tag or branch to use. Defaults to HEAD
      iscustom: [boolean]                     If the theme is a custom one, set as true.
```

### Example

```yaml

ohmyzsh:
  - user: "hrafn"
    updates:
      mode: "auto"
      frequency: "7"
      verbosity: "default"
    plugins:
      - name: "tmux"
      - name: "gradle"
      - name: "git"
      - name: "zsh-syntax-highlighting"
        repository: "https://github.com/zsh-users/zsh-syntax-highlighting.git"
      - name: "zsh-autosuggestions"
        repository: "https://github.com/zsh-users/zsh-autosuggestions"
    theme:
      name: "powerlevel10k"
      repository: "https://github.com/romkatv/powerlevel10k.git"
      iscustom: true
```
