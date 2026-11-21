# Rakesh Puttala – 3D Motion Portfolio

Static site: dark theme, scroll-scrubbed video background, Three.js particles.

## Structure
- `index.html` – page markup and metadata
- `css/style.css` – all styling and animations
- `js/main.js` – content data (skills, projects, research), video scrubbing, 3D particles, form, animations
- `assets/frames/` – 94 JPG frames extracted from the video (played by scroll position)
- `assets/video/original.mp4` – your original video (not loaded by the page)

## Run locally
Use any static server (needed so frames load reliably):
    python3 -m http.server 8000
Open http://localhost:8000

## Edit content
Open `js/main.js`: edit `S` (skills), `P` (projects), `R` (research), `C` (security activities).
Experience, GSoC details, hero text and contact info are in `index.html`.
Fill the "to be added" fields (GSoC organization/project/PR, Wipro duration, project statuses).

## Replace the video
Extract new frames at 960px width as `001.jpg`, `002.jpg`, ... into `assets/frames/`, e.g.
    ffmpeg -i new.mp4 -an -vf scale=960:-2 -q:v 9 assets/frames/%03d.jpg
Then set the frame count in `js/main.js` (`Array.from({length:94}`).

## Deploy
- Vercel: push this folder to GitHub, import the repo in Vercel, framework preset "Other", no build command.
- GitHub Pages: push and enable Pages on the main branch root.

## Notes
- Three.js loads from cdnjs and fonts from Google Fonts, so an internet connection is needed.
- The contact form opens the visitor's email app. A server-side email route is not included.
