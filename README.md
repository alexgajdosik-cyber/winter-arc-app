# Winter Arc Challenge Tracker

A simple 57-day habit tracker for the Winter Arc challenge (November 5 to December 31, 2026). It is a single HTML file with no build step and no dependencies, so it runs anywhere and is easy to host on GitHub Pages.

## Features

- **Task-by-day grid:** every habit has a row and every day has a column. Click a box to tick that habit for that day.
- **Daily progress line chart:** shows the share of your habits completed each day, with a 7-day average line. Click a point to highlight that day in the grid.
- **Ring charts:** a ring for today's tasks, a ring for every week (Monday to Sunday, final from Monday), a ring for every month, and a final ring with your total result for the whole arc. The final ring stays locked until January 1, 2027.
- **Progress bars:** an overall bar for the whole challenge, plus a bar for each habit showing how many days you completed it.
- **Stats:** current streak, best streak, perfect days, and overall completion.
- **Editable habits:** add or remove habits at any time. Changes apply to every day.
- **Light and dark mode:** follows your device setting.

## How it works

- The page compares today's date with November 5, 2026 to work out which day of the 57 you are on.
- The page follows the real date and weekday from your device's clock and shows today's date at the top. The grid's day numbers match the calendar, and today's column is outlined.
- Anyone can view the page at any time, but ticking only works from November 5 to December 31, 2026, and only for today's column. Before November 5 every box is locked, and after December 31 the page becomes a read-only record.
- Each day locks at midnight, so a missed day stays empty and cannot be filled in later.
- Your habits and ticks are saved in your browser's `localStorage`. There is no server and no account.
- Progress stays on one browser on one device. Clearing your browser data erases it, and opening the page on another device starts fresh.
- It runs on the honor system. The page records what you tick and cannot verify it. Locked days stop casual backfilling, but since data lives in your browser, clearing it or changing the device clock can still bypass the lock.

## Use it on your phone, offline

The app is a PWA (installable web app). After the first visit it is cached and works with no connection.

1. Put all the files in this folder on GitHub Pages (steps below). Phones need `https` to install and cache the app, so opening the file straight from storage will not give you offline caching.
2. Open the Pages link on your phone, once, while online.
3. **iPhone (Safari):** Share button, then **Add to Home Screen**. **Android (Chrome):** menu, then **Install app** / **Add to Home screen**.
4. Open it from the home screen icon. From then on it works in airplane mode.

Tips:
- Your ticks live on that phone. Use the home screen icon every time, not a mix of browser tabs and the icon, because they can keep separate storage.
- iPhone Safari may clear data of websites you have not opened for a while. The installed home screen app is protected from that.
- If you edit any file, change `CACHE` in `sw.js` (for example `winter-arc-v3`) so phones pick up the update.

## Run it locally

Download the files and open `index.html` in any browser. On a computer it works offline straight away, but installing and offline caching need `https` or `localhost` (for example `python3 -m http.server`).

## Put it online with GitHub Pages

1. Create a new repository on GitHub (for example `winter-arc`).
2. Add all the files from this folder (`index.html`, `sw.js`, `manifest.webmanifest`, the `.png` icons) to the root of the repository.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
5. Choose the `main` branch and the `/ (root)` folder, then click **Save**.
6. Wait a minute or two. Your site will be live at `https://<your-username>.github.io/<repo-name>/`.

## Customize

Open `index.html` in a text editor. Near the top of the `<script>` section:

- `DEFAULT_HABITS` is the list of starter habits. Edit the names to change them.
- `STORE` is the browser storage key. Change it if you want a completely fresh tracker.

Colors and fonts are defined as variables at the top of the `<style>` section.

The start date (`START`) and the length (`DAYS`) are near the top of the script. The chart's date labels are in the `renderChart` function, and weeks are real Monday-to-Sunday weeks, so the first one is short. If you want different dates, change them carefully everywhere or ask for help.

## Reset

Use the **Reset challenge** button at the bottom of the page. It asks you to click twice, then erases all progress and restores the starter habits.

## License

Released under the [MIT License](LICENSE).
