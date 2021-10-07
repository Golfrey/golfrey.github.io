---
title: hexo blog 101
date: 2021-10-06 22:44:56
tags:
- settings
- 101 series
categories:
- 101
description: This is a setup tutorial for user like me to re-setup their environment and re-learn something they already forgot. This one is for setting blog using github pages and hexo. 
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 

# Hexo Blog 101

## Make Sure you get Node.js environment

`node =v` & `npm -v` to make sure the environment is ok.

## Insall Git

`git --version` to make sure the environment is ok. 

Make sure you can connect to github ok.

`ssh -T git@github.com` should give you the right outcome.

See [git & github 101]() to see more about git.

## Install Hexo

`npm i Hexo-cli -g` to install Hexo.

`hexo -v` to check the environment ok.

## Publish new article

`hexo new [layout] <title>` `post` is the default layout. 

### Change Post layout

You can change files in scaffolds to change the default layout of post and draft.

```markdown
---
title: {{ title }}
tags:
categories:
description:
date: {{ date }}
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 
```

## Change Hexo Theme

### Download/Checkout theme into you project

Take vexo as an example

```bash
cd your-hexo-folder

git clone https://github.com/yanm1ng/hexo-theme-vexo.git themes/vexo

cp -R themes/vexo/_source/* source/
```

### Update project `_config.yml` theme config

```yaml
themes: vexo
```

### Modify theme `themes/vexo/_config.yml` with your own info

### Update Version

```bash
cd themes/vexo
git pull
```

## Backup Source Code to Github

We need to create a branch, called like hexo for example on our github page repo. We can git clone the repository to our computer and track the branch hexo. For example, `git branch -b hexo` , do things we like, then `git push origin hexo`.



## 