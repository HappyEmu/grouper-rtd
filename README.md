Grouper Documentation
====================

Deployed at: grouper.swissdrg.org (185.142.213.92)\
Directory: `/var/www/grouper-docs`

## Install
```
pip install sphinx sphinx_rtd_theme
```

## Build

```
make clean html
```

## Deploy

```
rsync -av build/html/ deployer@grouper.swissdrg.org:/var/www/grouper-docs/
```
