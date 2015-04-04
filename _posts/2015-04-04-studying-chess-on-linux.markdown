---
date: '2015-04-04 12:03:05'
layout: post
slug: studying-chess-on-linux
title: Studying chess on linux
categories:
- blog
---

I've been playing a lot more chess lately as it can be quite addicting. There are numerous places and ways to study chess, but I wanted to share a few things I've figured out from a linux perspective. I mostly play on [chess.com][] since I find their android app to be one of the better ones (though not without bugs). It doesn't really matter what service you use to play others so long as you are able to get the [Portable Game Notation (PGN)][PGN] file for your games. This contains a record of all the moves made in the game, you and the opponent's rating, and some other data.

One thing [chess.com][] doesn't have on it's web-based app that some other services do is a chess engine to evaluate positions when doing post-game analysis. Fortunately, you can do this yourself quite easily on linux if you have the game's [PGN][]. First, install [Scid vs. PC][scidvspc] which is a chess swiss army knife but importantly allows importing [PGN][] files and evaluating games with various chess engines. Basically if the chess engine exists and can be installed on linux, you can use it. [Stockfish][] is a very popular open-source chess engine and one of the engines I frequently use. Once you install it you can set up [Scid vs. PC][scidvspc] to analyze your games with it. Just go to `Tools → Analysis Engines → New` and add in stockfish using `stockfish` as the command and `$HOME/.scidvspc` as the directory. Make sure the protocol is UCI and you can give it a shortcut key or make it the default engine if you like.

Now just import a [PGN][] file by copying it to your clipboard and going to `Edit → Paste PGN → Import` and you've got the game loaded into the system. Click the little train engine above the board to get the chess engine going and scroll through the game with your mouse wheel. Now you can evaluate any chess game you can get a [PGN][] file for in real time. Pretty handy for improving your skills.

![Scid vs. PC](images/scidvspc.png)\ 

   [chess.com]: http://www.chess.com/
   [PGN]: http://en.wikipedia.org/wiki/Portable_Game_Notation
   [scidvspc]: http://scidvspc.sourceforge.net/
   [Stockfish]: https://stockfishchess.org/
