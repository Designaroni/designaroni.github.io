---
title: View Localhost On Devices In Your Network
date: 2016-11-06 06:00:00 Z
categories:
- terminal
tags:
- terminal
- code
- automation
layout: post
subtitle: Connect To Localhost Within Your Network
leadImage: "/assets/View_Localhost_On_Devices_In_Your_Network_26_9.jpg"
leadImageAlt: Connect To Localhost Within Your Network
forwardSlash: "/"
---

> Front End Pro Tip:

# View Localhost On Devices In Your Network

Often when I am working on `localhost` I want to test my work on other devices within my network. I typically would run `ifconfig` in the __terminal__ and peer through the lines of returned text for the the word `broadcast` then use the IP address from that line. Wanting an easier solution I put together the following shell script.

```
localIp() {
  ifconfig | grep -o {{site.singleQuote}}[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}{{site.singleQuote}} | head -2 | tail -1
}
```

I use `zsh` for my shell and have this housed in my `~{{site.forwardSlash}}.zshrc` file. Implementation is pretty straight forward. I also use __Atom__ most often for my editor

- Open your config file `atom ~{{site.forwardSlash}}.zshrc`
- Place in the function under the `# User configuration` line
- Reset available commands without needing to quit or restart terminal `source ~{{site.forwardSlash}}.zshrc`

Now you can run `localIp` and you should see something like this.

{{site.center}}
![Return Localhost Broadcast IP Address]({{site.baseurl}}/assets/local-ip-Nov-11-2016 16-14-06.gif)
{{site.endSpan}}

Lastly to run localhost on other devices load up the returned Ip address on your browser and optionally append the port or path you were working with before.
