# Aidan Scannell's Academic Website
Built using the [Academic Resume theme](https://github.com/wowchemy/hugo-documentation-theme) from [wowchemy](https://wowchemy.com/) and [hugo](https://gohugo.io/).

## Usage
### Create new content
1. Create a new project/publication/event(talk),
   ```
   hugo new --kind project project/<NAME-OF-PROJECT>
   ```
### Serve locally
To serve the site locally (at [http://localhost:1313/](http://localhost:1313/)) run,
```shell
hugo server --disableFastRender
```
or to include drafts use,
```shell
hugo server --disableFastRender -D
```

Sometimes we need to trash Hugo's cache with
```shell
$TMPDIR/hugo_cache
```

### Continuous deployment

Push to origin/main on GitHub to deploy to [www.aidanscannell.com](www.aidanscannell.com) using netlify.
