---
title: Digital Signage
path: /digital-signage
date: 2011-01-01
summary: Digital Signage for Everyone!
categories: [Development, Design]
tags: ["coding", "frontend", "design"]
image: images/home_signage.png
color: orchid
---

![background](/_images/home_signage.png)

# RPI Digital Signage

Links:

- [Raspberry Digital Signage](https://www.binaryemotions.com/raspberry-digital-signage/)
- [Raspberry Digital Signage - Documentation](https://www.binaryemotions.com/raspberry-digital-signage-docs/)
- [Raspberry Digital Signage - Plugins](https://www.binaryemotions.com/raspberry-digital-signage-plugins/)
- [Raspberry Digital Signage - Blog](https://www.binaryemotions.com/blog/)
<!-- - [Raspberry Digital Signage - Plugins](https://www.binaryemotions.com/rds.plugins/) -->
  

## Wordpress Plugin

From a SSH terminal of Raspberry Digital Signage (donors’), as root:

```bash
if ! grep -q bullseye /etc/apt/sources.list; then echo "deb http://raspbian.raspberrypi.org/raspbian/ bullseye main" >> /etc/apt/sources.list; fi
apt update
cd /root
wget https://www.binaryemotions.com/rds.plugins/raspberry-digital-signage-plugin-wordpress-18.0-1_all.deb
apt install -y /root/raspberry-digital-signage-plugin-wordpress-*.deb
```

## Prelude

I know you are likely short on time, so I try to keep things simple and concise. I'm a bit of a noob when it comes to Linux and RPI, because I'm playing with it every couple of years for a couple of days and then forget about it again. So please bear with me if I'm asking stupid questions or if I'm missing something obvious.
If you need more information, please let me know.

Here's what I'm trying to do and the problems I ran into:

We are a couple of people driving auto-busses for (mostly elder) people in our small city. This is all voluntarily and we are not getting paid for it. We are trying to make the busses more attractive and comfortable for the passengers. We are thinking about installing a small screen in the busses, which is showing the current location of the bus, the next stop, the time, the weather, etc... and maybe some news or other information. Programming of the stuff shouldn't be a huge problem (because I'm doing that for my living), but I'm not sure about the hardware and the software. I'm thinking about using a Raspberry Pi Zero W2, because it's small, cheap and has a built-in WiFi. I'm a huge fand of your Raspberry Digital Signage OS, but never had time to make real use of it.(until now ;))

So what I want to do in the end is running a local Wordpress instance on a Raspberry Pi zero W2, which is connected to a TV and running the Raspberry Digital Signage OS. This would be ideal, because my friends here are not that computer-proficient, but adding content to Wordpress is manageable for them. If I can't get this to work I'm thinking about using a simple HTML page with some sliders and gather the data from a Wordpress installation elsewhere (via REST-API) - but this is obviouls much more work in the end.

So with that beind said, here are a couple of questions/observations I have:

I followed the instructions from the [official documentation](https://www.binaryemotions.com/raspberry-digital-signage-docs/), which went fine - no problems.

Running local webpages is straight forward and works fine! (a pre-installed sftp would be nice, but I can live without it)
Also running remote webpages works fine, but is not ideal for my use-case.

But I had some issues with the installation of the Wordpress plugin.


## Issues

First of all, I couldn't (and still can't) access the WP-admin directly on the RPI. Likely this is intended, but you might want to let the users know about this. It took me quite a while of resetting Cookies, etc... on the RPI until I found out that I CAN access the WP-admin from my local machine easily. (the error message I got on the RPI was 'Cookies are blocked or not supported...' - messing with Chrome's settings didn't help)


### PHP
After I had the pre-installed Wordpress running, I noticed that I had to install some PHP extensions.
For Wordpress 6.4.3 and later, PHP 7.4 seems to be required to run without complaints. After running

```bash
apt-get install php7.4-xml
```

I could import some demo content. (I'm not sure if this is the only extension required, but it was the only one mentioned in the error message)

### PHP Extensions
Looking at Wordpress' `Site Health' section (in `Tools`) Wordpress 6.4.3 complained about some missing PHP extensions. The following extensions were mentioned:

- gd https://www.php.net/manual/en/book.image.php
- zip https://www.php.net/manual/en/book.zip.php
- curl https://www.php.net/manual/en/book.curl.php
- imagick
- mbstring
- intl

I didn't install anything special on the Wordpress instance, but some theme-builders and themes, also require these extensions. (mostly to let me import demo content and starter-assets and manipulate images).
Maybe it would be a good idea to at least install these PHP-extensions by default.

### Permalink structure
After I got everything running, I noticed that the permalinks were not working. I had to change the permalink structure to 'simple' (http://wordpress/?p=123), which seems to be the only link-structure working to navigate a multi-page Wordpress instalnce. Using anything else as permalink structure, just allows me to access the main page, but all other links are throwing a 404 error.

This also includes the REST-API. I can't access any of the endpoints.

Neither:

http://wordpress/wp-json/

nor 

http://IP-Address/wp-json/ are working.


### Postman Collection
Using the postman collection also took me a moment to figure out that I have to use RPI's IP address to access the REST-API. (which is obvious, but I didn't think of it at first). Maybe you could add a note about this to the documentation.

In the docs you write that we can drive the whole thing with the REST-API. But to me it is a bit unclear how so?
Can I pass e.g.:

```json
{
    "mousePointerDisabled": "no",
    "url": "http://wordpress",
}
```

to the 'kiosk' endpoint? Or do I have to pass the whole configuration (or all parts individually)? (I didn't try yet, because atm. it's working and I don't want to break it until I know how to restore everything :))

Is there some more in-depth documentation I am missing?


## General question/idea
Wouldn't it be much simpler to use `SQLite integration` for RDS-Wordpress? (It needs PDO, but otherwise makes things much more portable)

https://wordpress.org/plugins/sqlite-database-integration/

That's what I'm going to try out next... as soon as there's a little time left.


If you're still with me down here. Thanks a lot! It got a bit longer than expected, but I wanted to make sure I'm not missing anything obvious.

I'm looking forward to your feedback and I'm happy to provide more information if needed.

Cheers

andy





Lorem ipsum dolor sit amet, [consectetur adipisicing](https://google.ca) elit. Praesentium inventore hic possimus, cum nesciunt ea debitis, tempora officia perferendis vero ratione nam laudantium aliquid voluptatem velit? Open `/src/layouts.vue` and then edit the `main.css` file.

> Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic rerum earum quos explicabo suscipit maxime iste qui nihil `layout.vue` and then edit the `main.scss` file.

```js
<template>
  <Layout>
    <div class="container-inner mx-auto my-16">
      <h1 class="text-4xl font-bold leading-tight">{{ $page.post.title }}</h1>
      <div class="text-xl text-gray-600 mb-8">{{ $page.post.date }}</div>
      <div class="markdown-body" v-html="$page.post.content" />
    </div>
  </Layout>
</template>
```

Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic rerum earum quos explicabo suscipit. Praesentium inventore hic possimus, cum nesciunt ea debitis, tempora officia perferendis vero ratione nam laudantium aliquid voluptatem velit? Open `/src/layouts.vue` and then edit the `main.css` file.

Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic rerum earum quos explicabo suscipit. Praesentium inventore hic possimus, cum nesciunt ea debitis, tempora officia perferendis vero ratione nam laudantium aliquid voluptatem velit? Open `/src/layouts.vue` and then edit the `main.css` file.

```js
<script>
export default {
  props: ['totalPages', 'currentPage'],
  computed: {
    showPreviousPage() {
      return this.currentPage !== 1
    },
    previousPage() {
      return [0, 1].includes(this.currentPage - 1)
        ? this.base
        : `${this.base}/${this.currentPage - 1}`;
    },
    showNextPage() {
      return this.currentPage !== this.totalPages
    },
    nextPage(currentPage, totalPages) {
      return this.totalPages > this.currentPage
        ? `${this.base}/${this.currentPage + 1}`
        : `${this.base}/${this.currentPage}`;
    }
  },
  data() {
    return {
      base: '/blog'
    }
  }
}
</script>
```

---

## Typography

Here is how some typography styles are rendered:

# h1 Heading

## h2 Heading

### h3 Heading

#### h4 Heading

##### h5 Heading

###### h6 Heading

The quick brown fox jumps over the lazy dog

<s>The quick brown fox jumps over the lazy dog</s>

<u>The quick brown fox jumps over the lazy dog</u>

_The quick brown fox jumps over the lazy dog_

**The quick brown fox jumps over the lazy dog**

`The quick brown fox jumps over the lazy dog`

<small>The quick brown fox jumps over the lazy dog</small>

> The quick brown fox jumps over the lazy dog

[The quick brown fox jumps over the lazy dog](https://google.ca)

```php
<?php

class Foo extends bar
{
    public function fooBar()
    {
        //
    }
}
```

## Random Image

![mojave](/_images/mojave-night.jpg)
