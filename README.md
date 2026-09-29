# Number Zoomies

A speedy math facts game for kids: addition, subtraction, multiplication and division from 0 to 12, with sprint and survival rounds, per-player stats, fact-family tracking and optional voice answers.

**Play it:** https://richbowman-42.github.io/number-zoomies/

## Put it on an Android phone or tablet

1. Open the link above in **Chrome** on the device.
2. Tap the **⋮** menu, then **Add to Home screen** (or **Install app**), then **Install**.
3. Open Number Zoomies from the home screen. It runs full-screen and works without internet after the first visit.

Voice answers need Chrome and a microphone. The first time, allow the mic when asked.

## Moving a player's stats

Each device keeps its own players. On the **Who's playing?** screen, open **Move stats to another device**:

- **Save backup file** / **Load backup file** moves stats with a file (use Downloads, email, or Drive to carry it across).
- **Copy backup as text** / **Load pasted text** does the same through copy and paste.

Loading adds new players and merges ones with the same name. It never deletes anyone.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole game: layout, styles and code in one file |
| `manifest.webmanifest` | Name, icon and colors used when it's installed on a device |
| `sw.js` | Offline support. Bump `VERSION` inside it if you add or rename files |
| `icons/` | App icons |

## Trying changes on a computer

Any local web server works. With Python installed, from this folder:

```
python -m http.server 8000
```

Then open http://localhost:8000 in Chrome.
