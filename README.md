# Aidan Scannell's Academic Website
Built using the [Academic Resume theme](https://github.com/wowchemy/hugo-documentation-theme) from [wowchemy](https://wowchemy.com/) and [hugo](https://gohugo.io/).

## Usage
### Create new content
1. Create a new project/publication/talk,
   ```
   hugo new --kind project project/<NAME-OF-POST>
   ```
2. Export org sub-tree (a single blog post) to markdown in /posts/../ folder using C-c C-c H H
### Serve locally
To serve the site locally (at [http://localhost:1313/](http://localhost:1313/)) run,
```shell
hugo server --disableFastRender
```
or to include drafts use,
```shell
hugo server --disableFastRender -D
```

### Deployment

Pushing to =main= branch on GitHub will auto deploy to [www.aidanscannell.com](www.aidanscannell.com) using netlify.
