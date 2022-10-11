---
title: "Hugo Commands"
date: 2021-12-12T21:58:14-06:00
draft: false
category: Commands
tags:
- Blogging
- Hugo
---

## Create a new site

{{< highlight bash >}}
hugo new site quickstart
{{< / highlight >}}

## Add a theme

- [Hugo Themes](https://themes.gohugo.io/)
- Don't use the submodule method since that won't allow you to customize the theme.  Instead, download the zip file and extract into the themes directory.

{{< highlight bash >}}
cd quickstart
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
{{< / highlight >}}

## Add some content

{{< highlight bash >}}
hugo new post/my-first-post.md
{{< / highlight >}}

## Start the Hugo Server

{{< highlight bash >}}
hugo server -D
{{< / highlight >}}

## Site Configuration

Open up config.toml in a text editor

## Build static pages

{{< highlight bash >}}
hugo -D
{{< / highlight >}}

# Clone theme after git clone

{{< highlight bash >}}
git submodule init
git submodule update
{{< / highlight >}}