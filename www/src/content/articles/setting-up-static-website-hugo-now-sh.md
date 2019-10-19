---
date: 2019-01-20T10:18:00-00:00
description: "Here, I will explain you how to setup a static website with hugo and now.sh"
featured_image: "/images/pain.jpg"
title: "Setting up this blog with now.sh"
---

# Advantages of now cli

- Now cli is dead powerful
- Inexpensive

# Requirements

- Install hugo (macos)

{{< highlight bash >}}
brew install hugo
{{< / highlight >}}

- Install now cli

{{< highlight bash >}}
npm install now -g
{{< / highlight >}}

{{< highlight bash >}}
now login
{{< / highlight >}}

{{< highlight bash >}}
now domains add auggod.tech
{{< / highlight >}}

# Steps

- Setting up new site

{{< highlight bash >}}
hugo new site blog
{{< / highlight >}}

- Adding a theme

{{< highlight bash >}}
cd blog/themes
{{< / highlight >}}

{{< highlight bash >}}
git clone git@github.com:budparr/gohugo-theme-ananke.git
{{< / highlight >}}

- Configure site to use theme

{{< highlight bash >}}
cp gohugo-theme-ananke/config.toml ../../config.toml
{{< / highlight >}}

Now, you probably wants to change defaults values for config file.

Remove this line: `themesDir = "../.."`

- Adding a new article

{{< highlight bash >}}
hugo new articles/travel.md
{{< / highlight >}}

- Checking everything is right

{{< highlight bash >}}
hugo server
{{< / highlight >}}

- Compile assets
    
{{< highlight bash >}}
hugo
{{< / highlight >}}

- Create now.json

{{< highlight json >}}
{
  "version": 2,
  "name": "blog",
  "builds": [
    { "src": "public/**", "use": "@now/static" }
  ],
  "routes": [
    { "src": "/(.*)", "dest": "/public/$1" }
  ]
}
{{< / highlight >}}

- Push to now

{{< highlight json >}}
now
{{< / highlight >}}
