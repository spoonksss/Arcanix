<picture>
  <source media="(prefers-color-scheme: dark)" srcset="images/arcanix-logo-white.png">
  <source media="(prefers-color-scheme: light)" srcset="images/arcanix-logo-black.png">
  <img alt="Arcanix: your sovereign retro games vault." src="images/arcanix-logo-black.png" width="400">
</picture>

&nbsp;

![Arcanix](images/screenshot.webp)

> [!CAUTION]
> ***Disclaimer***
>
> *Arcanix was built entirely by vibe coding with **Claude Code**. I described what I wanted, step by step, and the AI wrote the code. I tested every part on my own PC, Android and handhelds and use it every day. A lot of care went into making it careful with your files. It never deletes a game file on its own, never overwrites your edits or saves by surprise, and always tells you plainly when something goes wrong.*
>
> *Still, it's a hobby project, provided **as is**, without any warranty. **Use it at your own risk**, and keep a backup of anything you can't afford to lose, like your games and saves.*

Arcanix is a ROM manager I built for myself, because I wanted one place for my retro games that works the same on all of my devices. It runs on a Windows PC, which I call **the host**. Three small companion apps connect to it:

- **Arcanix Mini** for Android
- **Mini Onion** for handhelds running Onion OS
- **Mini Knulli** for handhelds running Knulli

The idea behind it is simple. You point it at your games folder once, decide how you want things to behave, and after that it mostly runs on its own. It tries hard to do only what's needed, at the moment it's needed, and to stay quiet the rest of the time.

Below is what each part does, how it works, and the thinking behind it.

---

## 📚 Library

You choose one folder on the PC, the **Arcanix Games Root Directory**. Every folder inside it is a platform (for example `snes`, `psx`, `megadrive`), and every file inside those is a game.

- **It watches the folder.** When you copy games in, delete them or rename them, the library updates by itself. There's no Rescan button. It also waits until a copy has completely finished before it adds a game, so a half-copied file never turns up as a broken card.
- **Beautify Names.** Your platform folders often have short or technical names. Here you can give each folder the name you want to see in the app, for example `megadrive` shown as **Sega Mega Drive**. Your real folders are never renamed, and one switch flips between your names and the original ones.
- **Filtering.** You can leave out file types (like `.txt`), file names (like `Thumbs.db`) and folder names (like `Manuals`). A folder that ends up with no games is hidden everywhere in the app.
- **Platform descriptions.** Each platform page gets a short description, looked up once and kept.
- **Search** across the whole library, with suggestions while you type.

When the app starts it scans the folder once. After that, it only looks again when the folder actually changes. Restarting or reloading the page doesn't download anything again.

---

## 🖼️ Scraping: game info, artwork and logos

Scraping fills each game with its description, developer, release date, a large picture for the background (the hero) and a clean logo.

- **Where it comes from.** IGDB is asked first, for the text, the hero and the logo. Whatever IGDB doesn't have comes from a second source: Wikipedia for the text and SteamGridDB for the hero and logo. All of them are asked at the same moment, so you don't wait for one after the other. Answers that turn out not to be needed are dropped, not saved.
- **Picture quality.** A hero must be at least 1200 × 600, so nothing looks blurry on a big screen. IGDB's clean key art is preferred, and a screenshot is used only when there's no key art.
- **It never overwrites your data.** Scraping a game again only fills in what's missing. The one exception is **Force all**, which you choose on purpose, and which also replaces your own edits.
- **Bulk Scrape** works through the whole library and sorts the results into three lists you can act on: *Unscraped*, *No Results* (to try again) and *Partially* (to fill in only what's missing).
- **The Edit window** lets you change everything by hand: the text, the artwork and the logo (pick another one, or bring back the earlier one), and the game's RetroAchievements link.
- One switch, **Use scraping**, turns all of it on or off.

---

## 🏆 RetroAchievements

If you have a RetroAchievements account, Arcanix shows your profile, your recently played games and your progress.

- **Exact matching only.** A game is linked to RetroAchievements by its exact title. If the title doesn't match exactly, it isn't linked, because a wrongly matched game is worse than an unmatched one.
- **In the game window,** a pill switches between the game's description and its achievements with their badges. Arcanix remembers which of the two you like to see.
- **Achievement of the Week** shows as a slide on the home page, with the achievement, its badge and how many players have it. If the game is in your library, your own pictures and texts are used and nothing extra is downloaded. If it isn't, the game is scraped just for the slide, and those pictures are deleted when the next week's game arrives.
- **It asks RetroAchievements only when it has a reason:** your recent games on a timer while the app runs, a new week's achievement on Monday, a game's match when that game is scraped, and a full matching of the library only the first time or when your username, key or games folder changes. Switching the feature on or off, or reloading, never downloads anything again.

---

## 🎨 Appearance: your home page

The home page is yours to build.

- **The hero** is the large slideshow at the top. You choose how many slides it shows, which games it picks, and how often it picks new ones.
- **Sections** are the rows under it. Add as many as you like, drag them into any order, and give each a title. A section can be:
  - **Cards**, a row of game cards, in **Regular (2:3)**, **Wide (3:2)** or **Big (4:5)**
  - **Promo**, one wide banner for a single game
  - **Platforms List**, every platform with its number of games, including games that only your other devices have
- **What a row shows:** *Random games* from the folders you choose, *Curated games* (exactly the ones you pick, in your order), *Newest games*, or *Games with saves* (newest save first).
- **How often random rows change:** on every page load, every 2, 4, 8, 12 or 24 hours, or never. A small timer on the row shows when it will change next.
- Cards can show a **number** (1, 2, 3…) for "top" lists.
- **Light or dark theme**, and you can drag the Settings tabs into the order you prefer.

---

## 🔄 Syncer: keeping games in step

The Syncer keeps games in step between the host and your Android (Arcanix Mini). You decide **for each device** how it behaves:

- **Game lists only.** The device shows every game the others have, and you download just the ones you want.
- **One-way to the host.** The device's games are copied to the host.
- **One-way from the host.** The host's games are copied to the device.
- **Two-way Sync.** Everything is copied both ways.

How it handles the awkward cases:

- **Same name, different content.** You choose for each device: *Keep both* (the second one gets another name), *Newest wins*, or *Skip and ask me*. With the last one, the file waits in a list with three buttons until you decide: *Use my version*, *Use the new version* or *Keep both*.
- **Failed copies** are tried again immediately, after 3 seconds or after 10 seconds, as you set. Files that keep failing can be retried or set aside with one button.
- **Arriving games.** As soon as the lists are compared, games that only another device has appear as cards marked **"Arriving…"**, and each one becomes a normal game the moment its file lands.
- **Deletions are never passed on.** Deleting a game on one device never deletes it anywhere else. The only way to delete a game file is the **Delete Game** button in the Edit window, where you tick the devices yourself. A device that's offline deletes it as soon as it comes back, and until then you can still cancel.

**When it runs:** only when something changed. That means the host's folder changed, a device says its folder changed, a device comes back online, or you save new settings. It doesn't run on a timer, and it only ever copies what's missing.

---

## 📁 Saver: shared folders

Saver is for everything that isn't a game: screenshots, BIOS files, configs, notes, anything. You share a folder from one device, link it on the others, and Saver keeps it **exactly the same** on all of them.

- Each device chooses its own place for a shared folder.
- Every file and folder (empty ones too) moves both ways. The newest version wins, and a deletion is passed on to every device of that folder. That's the difference from the Syncer: this folder is meant to be a true mirror.
- **While a device is away,** the host holds on to only the files that device still needs (a small waiting room). Each file is deleted the moment no device needs it any more, and everything is deleted if that device unlinks or the folder is removed.
- The folder's owner can pause it for everyone.
- To keep your games safe, Saver **refuses** to share the games folder, a device's games folder, or a folder inside another shared folder.

---

## 💾 Archer: game saves everywhere

Archer collects the RetroArch saves of your devices (the host, Arcanix Mini, Mini Onion and Mini Knulli) and puts the newest save of each game on all of them. You play on a handheld, pick up the Android later, and your progress is already there.

**The tricky part, and the part I'm proudest of, is where the saves go.** RetroArch can store saves in very different ways from device to device. One device keeps a folder per emulator (`Genesis Plus GX/`), another a folder per platform (`megadrive/`), another puts saves right next to the games, and handhelds often have their own system. Some emulators even add a subfolder of their own (`fbneo/`). Copying a save to "the same path" on another device usually puts it somewhere the emulator will never look.

Archer handles this for you:

- **It recognizes every save by its game.** It knows which platforms each RetroArch emulator plays and how each handheld names its folders. So it can tell that `Genesis Plus GX/Sonic.srm` on the Android and `megadrive/Sonic.srm` on a Knulli are the same game's save.
- **It puts each save where that device already keeps saves of that system.** A Mega Drive save from a Knulli goes into the Android's `Genesis Plus GX` folder, because that's where the Android keeps its Mega Drive saves. An arcade save goes into the `fbneo` folder and never also into `neogeo`.
- **It never makes up a place.** Archer never creates folders. If a device has never saved a game of that system, it gets nothing until it saves one itself, and from then on Archer knows where its saves belong.

So you practically never have to move a save file by hand, and a save can't end up in the wrong folder.

The other details:

- **Every kind of save counts**, including RetroArch's `.srm` and the emulators' own files (memory cards, clocks, arcade saves). Save states don't.
- **Newest is decided carefully.** It isn't decided by comparing device clocks, which are often wrong on handhelds. Archer remembers each device's save at its last sending, so it knows which one really changed. A save whose date changed but whose content didn't is not sent again.
- **A device never gets its own save back,** and a newer save that hasn't been collected yet is never overwritten.
- **Archer never deletes a save by itself.** Collected saves stay, shown and downloadable, even when the game is gone and while Archer is off. Only the **Delete** button in Settings > Archer removes one, on every device.
- Each device decides for itself whether it takes part, and the host confirms each one.

---

## 🌍 Connectivity: your library from anywhere in the world

This is one of my favourite parts of Arcanix. Your games stay on your PC at home, yet you can reach them from a hotel Wi-Fi, a café or mobile data on the other side of the world. Arcanix Mini, Mini Onion and Mini Knulli work the same way away as they do at home: browse your library, download a game, send your saves, keep your folders in step.

### How it's possible: your own small server

Your home router doesn't let anyone from the internet in, and that's a good thing. To get past it safely, Arcanix uses **a small server that you rent online** (a cheap virtual server is plenty). The server works as a meeting point. It knows where your PC is and where your device is, and it introduces them to each other.

Setting it up takes one step. In **Settings > Connectivity > Allow Away from Home?** you type the server's address, a user name and a password, and press **Connect server**. Arcanix does the rest by itself:

- It logs in to the server, checks that it's suitable (Ubuntu 24.04 or Debian 12, with full admin rights), and installs its own small relay program there.
- It locks the server down. Its firewall opens only the few ports Arcanix needs plus your own login. An optional guard can block anyone who types a wrong password too many times (you choose how many tries and for how many hours). You can also move your login to another port.
- The relay program runs as its own user **with no rights at all**, keeps **no logs**, and downloads nothing by itself.
- Your password is used for the setup only. **It's never kept or written anywhere.**
- At the end, Arcanix checks that the server answers from the internet and tests whether **Direct** connections will work from your home (more on that below). The server's card then says either **"Direct ready"** or **"Server only"**.
- If anything goes wrong during the setup, Arcanix removes everything it had put on the server and tells you why.
- **Switching it off removes every trace of Arcanix from the server**: the program, its user, its files, the firewall rules, the guard and every package it added. The server is left exactly as it was before.

**Only your own devices can use it.** Every logged-in device gets its own pass, and the server turns away anyone else before doing any work for them. Everything between your device and your PC stays **encrypted end to end**. The server passes the data along but can never see inside it, and your PC's key never leaves your PC.

### The three ways a device connects

Each device always uses the best way available, in this order:

1. 🏠 **Local.** At home, on your own network. Always used when possible, and the server isn't involved at all. If a device is actually at home but asks the server anyway, the server sends it back to the home way.
2. ⚡ **Direct.** Away from home, the device connects **straight to your PC** over the internet. This is **always tried first** when you're away. It uses none of your server's traffic.
3. 🛰️ **Internet.** Only when Direct isn't possible, the data goes through your server. This is the one way that uses your server's monthly traffic, so the device's card turns orange to let you know.

Every device's card shows which of the three it's using right now.

### How Direct works

Normally, two devices behind two different home routers can't reach each other, because each router blocks anything it didn't ask for. Direct gets around this with a well-known trick, done carefully:

- The device asks your server, "where is my PC?" The server tells the device your PC's internet address, and tells your PC the device's address. That's all the server does.
- Then **both sides knock on each other's door at the same moment.** Each router sees its own side starting the conversation, so it lets the answer in. From then on, the device and your PC talk **directly**, and the server is out of the picture.
- This runs over a small, careful connection layer built into all four apps. It delivers every piece in the right order and checks that nothing is lost. Your normal secure connection runs inside it, with the PC's identity checked exactly as at home.
- If the routers on either side don't allow it, the device moves on to the **Internet** way by itself. You don't have to do anything.

### Keeping data use low, especially on the Internet way

When data passes through your server, every megabyte counts twice (once in, once out). For example, a 1 GB game uses up to 2 GB of the server's monthly traffic. So a lot of effort went into sending as little as possible:

- **Direct first, always.** The server only carries data when there's truly no other way.
- **The server mostly just rings the doorbell.** Your PC keeps one quiet line open to the server, and the server uses it only to say "a device wants you". Your PC then opens a line for that device. While nothing is happening, almost nothing is sent.
- **Nothing is downloaded twice.** The apps keep their game lists, pictures and logos on the device, each with a mark, and ask for them again only when the host says something changed. Opening Arcanix Mini or a handheld app away from home usually costs next to nothing.
- **Handheld pictures are made at their exact size** on your PC beforehand, so a handheld never downloads a bigger picture than it shows.
- **Devices never poll.** They don't keep asking "anything new?". They wait, and the host tells them when there's news.
- **Lost connections are noticed quickly** with tiny checks, so a broken line isn't left running.

### Guests

Guests are off unless you, the owner, allow them in Settings > Connectivity. When allowed, someone **on your home network** can open the host in a normal browser and enter as a guest, to look at and download your games. A guest can't change anything or see your settings, and the visit ends by itself after 15 minutes of not being used. Guests can never reach your host from outside your home: Direct and Internet are only for your own logged-in devices.

---

## 📱 Arcanix Mini (Android)

Arcanix Mini is the full Arcanix on your Android: the same home page, library, search, game windows and settings. It also takes part in the Syncer, Saver and Archer.

It keeps the platform lists, the game lists, the pictures and logos, the avatars and the Achievement of the Week pictures **on the Android itself**. Each one has a mark, and it asks for something again only when the host says that mark changed. Opening the app usually costs next to nothing, because everything is already there. Updating the app keeps all of it. Only uninstalling removes it.

## 🕹️ Mini Onion and Mini Knulli (handhelds)

Small native apps built for handheld screens and buttons.

- **Browse the host's library** platform by platform, with card pictures, and **download any game** straight onto the handheld.
- **The other way round:** games that only the handheld has appear on the host with a **Download** button. The handheld sends the game, and it lands in the right platform folder on the PC.
- **Pictures are made ahead on the host** at exactly the size of the handheld's cards, so the handheld never downloads more than it shows and never resizes anything itself.
- **Lists and pictures are kept** on the handheld until the host says they changed, so moving around is instant.
- **Archer** works on both.
- **Mini Knulli** also has a quiet background part. It keeps the connection, sends new saves, and shows small notes on Knulli's own menu, such as "Mini Knulli connected to the host".
- **Mini Onion** connects only while it's open.
- A **Menu** (Y button) with *Check for updates*, *Archer* and *Uninstall*.

---

## 📶 How it keeps data use low

This was a goal from the start, especially for handhelds on weak Wi-Fi and phones away from home.

- **Devices don't poll.** None of the apps asks "anything new?" on a timer. They connect when they come back (woke up, Wi-Fi returned, connection dropped), and otherwise they just listen. The host tells them when something changed.
- **Marks instead of re-downloads.** Every kept list and picture carries a mark, and it's fetched again only when that mark changes.
- **No refetching for nothing.** Reloading a page, restarting the app or flipping a setting doesn't download anything again.
- **Only what's used is collected.** Arcanix saves only data it actually shows or needs.
- **Exact-size pictures** for the handhelds, made once on the host.
- **The shortest path wins.** The home network first, then a direct connection, and your own server only as a last resort.

## 🔒 Privacy and safety

- Your data is kept in an **encrypted database**. A **recovery code** gets you back in if you forget your username or password.
- Everything runs over a **secure https connection** with the host's own certificate.
- Only the host's own window and Arcanix Mini can log in. A browser only gets in as a guest, and only if you allow guests.
- **Nothing is stored in the browser**, apart from one secure login cookie.
- **Auto-lock** after 15 minutes, 30 minutes, 1 hour, or never. You can see every logged-in device and log any of them out, or all at once.
- When something fails, you get a clear message saying what happened. Arcanix never quietly swaps in a guess or a default.

## 🧹 Nothing left behind

Temporary files, half-finished downloads, old pictures and leftover data are deleted the moment they're no longer needed, on every device. If the power goes out in the middle of something, the leftovers are cleaned up the next time that app starts.

## ⬆️ Updates

**Check for updates** is in Settings > General on the host and on the Android, and in the Menu on the handhelds. It looks at this GitHub page, and if there's a newer version it updates **the host and the app on that device** together. Before it starts, it warns you that anything currently being copied will be cut off and has to be started again.

---

## 📥 Getting started

1. Download the files from the [Releases](https://github.com/spoonksss/Arcanix/releases) page.
2. **On the PC:** run `Arcanix-Setup-<version>.exe`, create your account and choose your games folder.
3. **On Android:** install `Arcanix-Mini-<version>.apk`.
4. **On Knulli:** unzip `Mini-Knulli-<version>.zip` onto the root of the games partition, the one with the roms and system folders.
5. **On Onion OS:** unzip `Mini-Onion-<version>.zip` onto the root of the SD card.
6. **Arcanix Mini:** log in with your Arcanix account. **Handhelds:** open Mini Knulli from Ports or Mini Onion from Apps, and approve its request in the host's window.

---

## 🛠️ Under the hood

- **The host:** a Python backend and a React + Vite frontend. The frontend follows its own design system, and every build is checked so no screen strays from it.
- **Arcanix Mini:** a native Android app.
- **Mini Onion and Mini Knulli:** small native C programs with their own secure connection code, made to run on low-power handhelds.

---

## 📜 License

Arcanix, Copyright (C) 2026 Dimitar Tsonov. Licensed under GNU GPLv3.

You're free to use, change, rebuild and share Arcanix. If you share a changed version, its code must be shared too, under the same license. See [LICENSE](LICENSE).

Parts made by others, like the Archivo font, keep their own licenses.
