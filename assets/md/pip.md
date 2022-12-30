# pip

## Package management

- `pip3 freeze --user | sed "s/=.*//"` List all user packages without version number
- `pip3 freeze --user 2> /dev/null | sed 's/==.*//' | xargs pip3 uninstall -y` Uninstall all user packages
- `pip3 list --outdated --format=freeze | grep -v '^\-e' | cut -d = -f 1  | xargs -n1 pip3 install -U` Upgrade all outdated packages
- `pip3 freeze --local | sed "s/=.*//" >> requirements.txt` list all package in virtural env and redirect to requirements.txt

## Cache
- `rm -rf ~/.cache/pip/*` Clear pip cache in Linux
- `rm -rf ~/Library/Caches/pip/*` Clear pip cache in macOS
