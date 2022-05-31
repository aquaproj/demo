# demo

## Demos

https://aquaproj.github.io/docs/demo

* https://asciinema.org/a/457021
* https://asciinema.org/a/498262

## Prepare for demo

* Checkout this repository
* Uninstall aqua
* Remove gh and conftest including symbolic links

```
$ mv ~/.local/share/aquaproj-aqua ~/.local/share/aquaproj-aqua.bak
$ brew uninstall aqua
```

## Scenario

```
: Install aqua
brew install aquaproj/aqua/aqua
aqua -v
export PATH="${AQUA_ROOT_DIR:-${XDG_DATA_HOME:-$HOME/.local/share}/aquaproj-aqua}/bin:$PATH"

: Install tools
gh version
cat aqua.yaml

: Install GitHub CLI
aqua init
cat aqua.yaml
aqua g -i cli/cli
cat aqua.yaml
aqua i
gh version
which gh

: Search tools
aqua g -i
cat aqua.yaml
: conftest is not installed yet
conftest -v
: create only symbolic link
aqua i -l
: tool is installed automatically when tool is run
conftest -v

: Change tool version
vi aqua.yaml
conftest -v
: update was reflected automatically.

: Change tool version per project
cd project-a
cat aqua.yaml
conftest -v
cd ../project-b
cat aqua.yaml
conftest -v
cd -
conftest -v
cd -
conftest -v
: tool version was changed seamlessly

: aqua refers configuration file recursively
cat aqua.yaml
gh version
cat aqua.yaml

: Global Configuration
cat ../dotfiles/aqua.yaml
tfmigrator -v
: Set AQUA_GLOBAL_CONFIG
export AQUA_GLOBAL_CONFIG=$PWD/../dotfiles/aqua.yaml:${AQUA_GLOBAL_CONFIG:-}
aqua i -l -a
tfmigrator -v
```

## LICENSE

[MIT](LICENSE)
