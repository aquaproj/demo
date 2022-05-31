# demo

## Prepare for demo

* Checkout this repository
* Uninstall aqua
* Remove gh and conftest including symbolic links

## Scenario

```
: Install aqua
brew install aquaproj/aqua/aqua
aqua -v
export PATH="${AQUA_ROOT_DIR:-${XDG_DATA_HOME:-$HOME/.local/share}/aquaproj-aqua}/bin:$PATH"

: Install tools
gh version
cat aqua.yaml

: Install gh
aqua init
cat aqua.yaml
aqua g -i cli/cli
cat aqua.yaml
aqua i
gh version
which gh

: Check actual install path
aqua which gh

: Search tools
aqua g -i
: conftest is not installed yet
conftest -v
: create only link
aqua i -l
: tool is installed automatically
conftest -v

: Change tool version
vi aqua.yaml
conftest -v
: update was reflected automatically.

: Change tool version per project
cd project-a
cat aqua.yaml
conftest --version
cd project-b
cat aqua.yaml
conftest --version

: aqua refers configuration file recursively
gh version

: Global Configuration
cat dotfiles/aqua.yaml
tfmigrator -v
export AQUA_GLOBAL_CONFIG=$PWD/dotfiles/aqua.yaml:${AQUA_GLOBAL_CONFIG:-}
aqua i -l -a
tfmigrator -v
```

## LICENSE

[MIT](LICENSE)
