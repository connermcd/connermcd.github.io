---
date: '2015-03-31 18:29:00'
layout: post
slug: replacing-goobook-and-notmuch-with-mu
title: Replacing goobook and notmuch with mu
categories:
- blog
---

In a [previous post](http://connermcd.com/blog/2012/09/25/using-mutt-with-offlineimap-and-vim.html) regarding [mutt][] I recommended [notmuch][] for searching mail and [goobook][] for accessing contacts. For some time now I've replaced both of these tools with a different tool called [mu][] that accomplishes both tasks quite efficiently.

[mu][] provides indexing for Maildir and has several command-line options for searching mail, extracting attachments, exporting contact lists and much more. Consequently it works quite well with [offlineimap][] and [mutt][]. There's very little change needed to implement it and in my experience it is much better at searching mail than [notmuch][] and much quicker at getting contact info than [goobook][].

I made these changes to my [.offlineimaprc](https://github.com/connermcd/dotfiles/blob/master/.offlineimaprc.template) and [keybinding](https://github.com/connermcd/dotfiles/blob/master/.mutt/keybindings) files:

## .offlineimaprc
```
[Account Gmail]
...
postsynchook = mu index --maildir ~/.mail
```

## .muttrc
```
bind editor <Tab> complete-query
set query_command = "mu cfind --format=mutt-ab  '%s'"
macro index Z "<shell-escape>mu find --clearlinks --format=links --linksdir=~/.mu/results " "mu find"
macro index S "<change-folder-readonly>~/.mu/results<enter>" "mu find results"
```

Just download [mu][] and follow its simple instructions to index your maildir then add these changes to your config files. Now [offlineimap][] will run [mu][]'s indexer at the end of each sync and when you start a new email in [mutt][] you can hit tab to complete recipients. If you want to search mail you can use my Z binding and utilized [mu][]'s many search features. That's it!

   [mutt]: http://www.mutt.org/
   [notmuch]: http://notmuchmail.org/
   [goobook]: http://pypi.python.org/pypi/goobook/1.4alpha4
   [offlineimap]: http://offlineimap.org/
   [mu]: http://www.djcbsoftware.nl/code/mu/
