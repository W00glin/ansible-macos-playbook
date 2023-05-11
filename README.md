# Ansible MacOS Playbook 

Howdy, This is the playbook I use after a clean install of MacOS to get *most* of everything setup.

I more or less use this a baseline to save me from having to manually install a bunch of programs. 
## Roles/Tasks
In use -

- Installs Homebrew packages and app casks (Role `homebrew`)

Not currently in use -

- Installs App Store apps with [`mas-cli`](https://github.com/mas-cli/mas) (Role `mas`) - 
- Modifies MacOS settings (Role `settings`)
- Changes the user shell, if configured (Role `shell`)

## Installation

1. Install [Homebrew](https://brew.sh) from this site. Review documentation to make sure you understand it.

You can also install it with -

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
2. Once `homebrew` is installed you will then need to install `ansible`

Run the following -
```shell
brew install ansible
```
Check to see if `ansible` installed correctly by running -

```shell
ansible --version
```
You should see an output similar to -
```
ansible [core 2.14.5]
  executable location = /opt/homebrew/bin/ansible
  python version = 3.11.3 (main, Apr  7 2023, 20:13:31) [Clang 14.0.0 (clang-1400.0.29.202)] (/opt/homebrew/Cellar/ansible/7.5.0/libexec/bin/python3.11)
  jinja version = 3.1.2
  libyaml = True
```
If you see that, it is installed.

3. Running the playbook
If you have not already you will want to tweak/configure the `default.config.yml` to install whatever applications you would like. This fork/repo represents tools I would like installed.

Don't skip this, otherwise your computer will be provisioned just like mine.

This first command copies the repo ansible config into another one called `config.yml` probably not needed, but good practice.
```shell
cp default.config.yml config.yml
```

This second command will review the changes being applied to your machine
```shell
ansible-playbook --check main.yml
```

This command will actually run the playbook -
```shell
ansible-playbook main.yml
```

## Updating a fork with the latest changes from this repository

If you forked this repository and want to include its latest changes without losing your own,
add this repository as an upstream and rebase it onto your fork:

```bash
git remote add upstream git@github.com:jeromegamez/ansible-macos-playbook.git
git fetch upstream
git rebase upstream/main
```

## Acknowledgements

This playbook is heavily inspired by
[Jeff Geerling's mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook).