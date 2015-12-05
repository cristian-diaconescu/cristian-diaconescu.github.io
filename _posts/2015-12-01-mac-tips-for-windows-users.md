---
layout: post
title: Mac tips & shortcuts for Windows users 
categories: mac tips-and-tricks productivity
---

I'm a Windows user. I grok Windows. It feels at home. When I open a Mac, it feels alien. There are things I like right off the bat - a nice screen, a backlit keyboard, good battery (yes please!) and many UI metaphors are just the same 

When using an iPhone for the first time, things are immediately obvious. It's optimized for discoverability. With Macs (and OS X), well... it's more complicated. It's optimized for efficiency (I guess). 

But in order to be efficient, you need to do common tasks using **muscle memory**, which requires training, which takes time. Even more so if you have to stop every so often to google how to do this-and-that on a Mac.  
So I'm writing this article as a one-stop-shop for your (and my) ramp-up.

## Common keyboard shortcuts

If you use a common keyboard shortcut in Windows, like `Ctrl-S`, chances are it will work in OS X. Just substitute `Ctrl` with `Cmd`.  
The `Cmd` key is the one with the little "flower doodle": ⌘

These just work:

- `Cut`, `Copy`, `Paste`, `Select all`
- `Save`, `Undo`
- `Bold`, `Italic`
- `New`, `Open`, `Print`
- Just about every shortcut in Adobe Photoshop. It was built for Macs first, after all.

## Switching apps and windows

In Windows, `Alt-Tab` goes through all open **windows**, regardless if they belong to the same application or not.

In OS X, the closest equivalent is `Cmd-Tab` - but it only switches **applications**. If you have 3 Chrome windows open, and nothing else, `Cmd-Tab` will do nothing (all windows are part of the same application - Chrome)

There is another, less known shortcut that switches *only* between windows of the same application: ``Cmd-` ``. That's the `backtick` key and it is usually located above the `Tab` key. This shortcut ignores minimized windows.

There's another way to select one of the windows of the currently active application: the "3-finger swipe down" gesture shows all windows of the application, including minimized ones. 

## Nomenclature for similar notions

Windows | Mac
---------|---
Task bar | Dock
Tray (bottom-right corner) | Status menus (top-right corner) 
Start menu (for a list of installed programs) | Launch Pad (rocket icon) or do a pinch gesture with thumb+three fingers
Start menu (for typing to filter things by name) | Spotlight (`Cmd-space` or magnifier icon in the top-right corner)
Shutdown/Restart/Logoff | Apple menu (top left)

### Common programs

Windows | Mac
---------|---
Windows Explorer | Finder (look for the half blue / half white face)
Notepad | Nothing. See below.
Wordpad | TextEdit. If you want to save plain text (like Notepad): `Format > Make plain text`
Task manager | Activity Monitor
Resource Monitor | Activity Monitor
Command Prompt | Terminal
Solitaire | Nothing built-in (the shock! the horror!) But you can [play tetris in text mode inside Emacs](http://computers.tutsplus.com/tutorials/how-to-play-tetris-pong-and-other-hidden-games-on-your-mac--mac-44485) for major geek points!

## Closing things

There are a dozen ways to close documents, applications, tabs, popups and whatnot. This is one of the places where Macs are just... *different*.

The most obvious one is the little red round **x** button in the top-*left* corner of most any window.

It does something different in OS X than in Windows: it closes the *current* window, but not the application - not even if the application only ever *has* one window. 
 
You can quickly tell which apps are running by the little dot under their icon in the *dock*.

![active apps in dock]({{ site.baseurl }}/public/img/mac-dock-active-apps.png)

If you want to really close the *application*, you need to right-click (or `Ctrl-click`) its dock icon and click `Quit`.

To recap:

Action | Win    | Mac
-------|--------|----
Close current document/tab   | `Ctrl-F4` | `Cmd-W` (but leaves the application running)
Close application    | `Alt-F4` | `Cmd-Q`

## Moving through text with the keyboard

Action | Win    | Mac
-------|--------|----
Beginning/end of row| Home/End | Cmd-left/right
Jump over a word | Ctrl-left/right | Alt-left/right
Prev/next page | Page up/Page down | fn-up/down
 
## Deleting text

There's no **Del** key on my Macbook!  

The key known to Windows users as `Backspace` is called `Delete` in OS X. It deletes text to the *left* of the cursor (like `Backspace`) 

In order to delete text to the right of the cursor (like `Del`), use the combination `fn - Delete`.

## Finder

### Deleting files
Action | Win    | Mac
-------|--------|----
Move file to trash | Delete | Cmd-Delete
Permanently delete file | Shift-Delete | nothing built-in, just empty the trash after deleting


## Chrome

Some of the actions I use most in Chrome don't have a 1:1 mapping between Windows and OS X. Sigh.

Action | Win    | Mac
-------|--------|----
Refresh | F5 | Cmd-R
Switch between tabs | Ctrl-Tab/Ctrl-Shift-Tab | Cmd-Alt-left/right


## Neat features only found in OS X
### Previous versions of a document

I was blown away by how well integrated this feature is. As far as I know, there's nothing as streamlined in Windows. 

 In most applications that deal with documents, go to `File > Revert to > Browse All versions` and find all the previous versions of the document you're working with, neatly displayed, one for every time you pressed `Save`.
 
## The tip of the iceberg
 
 The points I have touched are just things off the top of my tired, sleepy head late at night. 
 I'm pretty sure I have missed things I do regularly. 
 
 And I am *certain* there are so many tricks that I simply don't know.
 
 I would love to hear about *your* favourite tricks in the comments! You know... *learn and let learn*.
 