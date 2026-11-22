# 📖 How to use Arcanix

Each part says what it does, how to set it up, and what is good to know. Back to the [main page](README.md).

---

## 📚 Library
All your games in one place.

### How to use it
- **The host:** Settings > Storage, press Browse and choose your games folder. Each folder in it is a platform (like `snes`), and each file is a game.
- **The Android and the handhelds:** nothing to set up. They show the host's library.

### Good to know
- New, deleted or renamed games show up by themselves.
- A game is added only after it has finished copying.
- **Beautify Names:** show `megadrive` as **Sega Mega Drive**. Your folders are never renamed.
- **Filtering:** hide files and folders you don't want to see, like `.txt` files or a `Manuals` folder.

---

## ⬇️ Getting a game onto a device

### The Android
- **Syncer on:** press **Download**. The game goes straight into the right folder.
- **Syncer off:** press **Download Game**. It lands in the Android's Download folder. Move it into your emulator's folder yourself.

### The handhelds (Knulli and Onion)
1. Open Mini Knulli (in Ports) or Mini Onion (in Apps), pick a game and press A.
2. Choose **Download game**, **Download save** or **Download both**.
3. It lands in the **Downloads** folder, in a folder named after the platform. Downloads is next to your roms folder.
4. Move it into that platform's roms folder yourself. On Knulli, then press Start > Game Settings > Update Gamelists.

### From a device to the host
- A game only the Android or a handheld has shows on the host with a **Download** button. Press it, and the game lands in the right folder on the PC.

---

## 🖼️ Scraping
Fills every game with its description, a big background picture and a logo.

### How to use it
- **The host:** Settings > Integrations, switch on Use scraping, add your SteamGridDB key, Save Changes.
- **Bulk Scrape** fills the whole library. The **Edit** window does one game.

### Good to know
- It looks in IGDB first, then in Wikipedia and SteamGridDB for what is missing.
- It never overwrites your data. Only **Force all** does, and only when you choose it.
- In the **Edit** window you can change the text, pictures and logo by hand.

---

## 🏆 RetroAchievements
Your profile, recent games and progress, right in your library.

### How to use it
- **The host:** Settings > Integrations, switch on Use RetroAchievements, type your username and key, Save Changes.

### Good to know
- A game is linked only when its title matches exactly.
- In a game's window, a pill switches between its description and its achievements.
- The **Achievement of the Week** shows as a slide on the home page.

---

## 🎨 Appearance
Build your own home page.

### How to use it
- **The host or the Android:** Settings > Appearance. Add rows, drag them into order, Save Changes.

### Good to know
- On top is a slideshow. You choose how many games it shows and how often they change.
- Each row can be game cards, one wide banner, or a list of platforms.
- A row can show random games, games you pick, the newest games, or games with saves.
- Choose a light or dark theme.

---

## 🔄 Syncer
Keeps your games the same on the host and your Android.

### How to use it
1. **The host:** Settings > Syncer, switch on Use the Syncer, Save Changes.
2. **The Android:** Settings > Syncer, switch on Use the Syncer, choose its games folder, Save Changes. It shows a code.
3. **The host:** press **Confirm** when the same code shows. Choose a way to sync and press Save Changes.

### The ways to sync
- **One-way to Arcanix:** The Android's games are copied to the host.
- **One-way from Arcanix:** The host's games are copied to the Android.
- **Two-way Sync:** Both get every game.
- **Game lists only:** Nothing is copied, and you download only the games you want.

Knulli and Onion handhelds are never synced, but their games always show on the host.

### Good to know
- **Deleting a game by hand never deletes it anywhere else.** It is never copied back either: it stays as a card with a **Download** button.
- To delete a game on other devices too, use **Delete Game** in its Edit window. Its small cog chooses where.
- A device that is away deletes it the moment it comes back.
- **The same game, two different files:** choose **Keep both**, **Newest wins** or **Skip and ask me**.
- Games coming from another device show as **"Arriving…"** until they land.
- Arcanix never deletes a game on a handheld.

---

## 📁 Saver
Keeps any folder the same on all your devices: screenshots, BIOS files, configs and more.

### How to use it
1. **The host or the Android:** Settings > Saver, press **+**, give it a name, choose the folder, press **Add Folder**.
2. **Your other devices:** press the folder's link icon, choose a folder there, Save Changes.

The handhelds don't use Saver.

### Good to know
- It is a true mirror: delete a file, and it is deleted on every device. The newest file always wins.
- It never touches your games. It refuses every games folder.
- A device that is off gets the changes when it is back.
- The folder's owner can pause it for everyone.

---

## 💾 Archer
Your game saves follow you. Save on a handheld, continue on the Android.

### How to use it
- **The host:** Settings > Archer, switch on Use Archer, Save Changes. To include the PC's own saves, also choose RetroArch's saves folder.
- **The Android:** Settings > Archer, choose RetroArch's saves folder, switch on Use Archer, Save Changes. Press **Confirm** on the host when the same code shows.
- **The handhelds:** press Y for the Menu and switch on Archer. Press **Confirm** on the host.

### Good to know
- Every device gets the newest save of each game.
- A save lands only where that device already keeps saves of that system. For example, a Mega Drive save from a Knulli lands in the Android's `Genesis Plus GX` folder.
- No saves of that system on a device yet? Play and save once there. From then on, saves arrive by themselves.
- Archer never creates folders and never deletes a save. Only **Delete** in Settings > Archer does.
- Save states are not included.

---

## 🌍 Connectivity
Reach your library from anywhere, through your own small server. Your games stay at home.

### How to use it
- **At home:** nothing to set up.
- **Away from home:** rent a small server (Ubuntu 24.04 or Debian 12). On the host, go to Settings > Connectivity > Allow Away from Home?, type its address, user name and password, and press **Connect server**. Every device then works away from home by itself.

### Good to know
- Arcanix sets up the server and locks it down by itself. Your password is never kept.
- Switching it off removes everything Arcanix put on the server.
- Only your own devices can use it, and everything stays encrypted.
- Each device picks the best way by itself:
  - 🏠 **Local:** at home, on your own network.
  - ⚡ **Direct:** away from home, straight to your PC. It uses none of the server's traffic.
  - 🛰️ **Internet:** through your server, only when Direct isn't possible. The device's card turns orange.
- **Guests:** allow them in Settings > Connectivity. Someone on your home network can then open the host in a browser, look at your games and download them. Guests can't change anything.

---

## 📱 Arcanix Mini (Android)
The full Arcanix on your Android: the home page, library, search and settings. It takes part in the Syncer, Saver and Archer.

## 🕹️ Mini Knulli and Mini Onion (handhelds)
Small apps made for handheld screens and buttons, to browse the host's library.
- **Mini Knulli** stays connected in the background. It sends new saves and shows small notes on Knulli's menu.
- **Mini Onion** connects only while it is open.
- Press **Y** for the Menu.

---

## 📶 Light on data
- Lists and pictures are kept on each device and downloaded again only when they change.
- The handhelds get pictures made at their exact size.
- Devices never keep asking for news. The host tells them.
- The home network comes first, then Direct, and your server only as a last resort.

## 🔒 Privacy and safety
- Your data is kept encrypted. A recovery code gets you back in.
- Every connection is secure.
- Only the host's window and Arcanix Mini can log in.
- Auto-lock, and you can log out any device.
- When something fails, you get a clear message. Never a guess.
- Nothing is left behind: leftover files are deleted on every device.

## ⬆️ Updates
- **Check for updates** is in Settings > General on the host and the Android, and in the Menu on the handhelds. It updates the host and that device's app together.
- **Include pre-releases**, right next to it, also offers test versions. One switch sets it for every device.
- Always update the host and every app together.
