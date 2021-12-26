---
layout: post
title:  "Restore Discord's old icon on Linux"
description: "Restoring Discord's old icon, because the new one sucks."
keywords: discord,linux,old icon,discord redesign
date:   2021-12-26 14:55:00 +0200
---

Just a quick how-to if you, like me, hate the new icon.

# Find out where Discord is installed

On KDE Plasma, right-click on Discord in the app launcher and click "Edit Application...".
Switch over to the "Application" tab, and look at the "Command: " field.
The file it's pointing to may be a symlink, so run `ls -l path`, for me `path` was `/usr/bin/discord`:

```shell
$ ls -l /usr/bin/discord
lrwxrwxrwx 1 root root 20 09-22 21:03 /usr/bin/discord -> /opt/discord/Discord
```

So in my case, the directory where my Discord client is installed it `/opt/discord/`.

# Replace the icon

Get the icon from [here](/assets/2021/12/26/discord.png) and put it in an accessible location like your home directory.

Then, open a terminal in your installation directory. Let's back up the current icon:

```shell
sudo mv discord.png discord-new.png
```

Now let's actually replace the icon:

```shell
sudo mv path_to_new_icon discord.png
```

Replace `path_to_new_icon` with wherever you put the downloaded icon,
if you put it in your home that'd be `/home/$USER/discord.png`.

# Refresh icon cache

You're basically done: you just need to refresh the icon cache.
Log out, then log back in. If that doesn't work, restart. If *that* doesn't work,
search for "\[YOUR_DESKTOP_ENVIRONMENT\] refresh/clear icon cache".

That's about it!
