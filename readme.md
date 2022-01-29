# Introduction

## Run locally

To run the jekyll local, uncomment the theme line and comment the remote_theme line as showed bellow.

```yml
#remote_theme              : pmarsceill/just-the-docs
theme                     : just-the-docs
```

And start the jekyll with following command:

```bash
$ bundle exec jekyll serve
```

## Publish on github pages

To publish the documentation remotely, comment the theme line and uncomment the remote_theme line as showed bellow.

```yml
remote_theme              : pmarsceill/just-the-docs
#theme                     : just-the-docs
```

Push the changes to the ai-blox.github.io site.

```bash
$ git push
```

And check if the deployment went successful: https://github.com/ai-blox/ai-blox.github.io/deployments


