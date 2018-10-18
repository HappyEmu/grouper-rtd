Grouper Documentation
====================

# Build

```
make clean html
```

# Deploy

```
rsync -av build/html/ deployer@grouper.swissdrg.org:/var/www/grouper-docs/
```
