# Morse Trainer

A browser-based Morse code trainer inspired by a pocket letter-tree trainer. Built with plain HTML, CSS, and JavaScript; no dependencies or build step.

## Run

Open `index.html` in a modern browser, or serve this directory:

```sh
python -m http.server 8000
```

Then visit http://localhost:8000.

## Controls

- Hold **Space** or the **Transmit** button. A short press sends a dot; a longer hold sends a dash.
- The letter and tree update while you hold the key, switching from dot to dash at the timing threshold.
- Set **Pace** from 5 to 60 WPM. Toggle the 600 Hz tone with **Sound on**.
- Use **Word space**, **Delete letter**, and **Clear** to edit the decoded message.
- Mouse and touch input are supported.

## Timing and letter recognition

One timing unit is `1200 / WPM` milliseconds. A press shorter than two units is classified as a dot; a press of two units or longer is a dash. The intended rhythm is one unit for a dot and three units for a dash. A three-unit pause ends a letter.

This trainer also includes an A–Z learning aid:

- A letter with no longer valid continuation finishes immediately on release.
- If another signal cannot extend the current letter into a valid A–Z code, the current letter finishes and that signal starts the next letter.
- Other letter boundaries still use the pause duration.

This automatic splitting is a training aid, not a general Morse decoder for digits or punctuation. At high speeds, input precision depends on the browser, device, and operating system.

## Project files

- `index.html`: interface, responsive styling, and SVG letter tree container.
- `app.js`: Morse mapping, live tree rendering, input timing, sound, and decoding.

Everything runs in the browser. No account, backend, or external service is required to run the app. Random-word practice is not implemented.
