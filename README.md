A lightweight, real-time technology news website that aggregates headlines from multiple free public APIs into one clean, searchable feed. Built with plain HTML, CSS and JavaScript. No backend, no build step and no API keys required.

Abstract

Technology news is scattered across developer communities, code-hosting platforms and specialised publications, so keeping up means checking many sites every day. Tech Pulse solves this by pulling live data from several free public APIs directly in the browser, normalising it into a single format, and presenting it as one unified, mobile-friendly feed.

The application fetches stories from four sources: Hacker News (top stories), DEV Community (top articles), GitHub (newly created, fast-growing repositories) and the Spaceflight News API (space and hardware news). Each source returns data in a different shape, so a small adapter layer converts every response into a common structure (title, link, source, timestamp, summary, image, engagement note). The "All" view merges the sources and sorts them by recency, while individual tabs let readers focus on one source.

The project is a single static file, so it can be hosted for free on GitHub Pages, Netlify, Vercel or Cloudflare Pages, and it needs no server, database or paid service. It is a practical example of consuming REST APIs, handling asynchronous requests, graceful error handling and responsive UI design with vanilla web technologies.

Features
Live news from four free, keyless APIs
"All" view that merges and sorts every source by time
Per-source tabs: Hacker News, DEV, GitHub Trending, Space & Hardware
Instant headline search and filter
"Show more" pagination
Automatic refresh every 10 minutes, plus a manual Refresh button
Light and dark themes, with the choice remembered
Loading placeholders and a saved-copy fallback if a source is unreachable
Responsive layout, keyboard-focus styles and reduced-motion support
External links open in a new tab with noopener noreferrer
Data Sources
Source	Endpoint	Key needed
Hacker News	hacker-news.firebaseio.com/v0	No
DEV Community	dev.to/api/articles	No
GitHub Search	api.github.com/search/repositories	No (about 60 requests/hour per visitor)
Spaceflight News	api.spaceflightnewsapi.net/v4/articles	No
Tech Stack
HTML5, CSS3 (custom properties, grid, flexbox)
Vanilla JavaScript (ES2020, fetch, async/await)
Google Fonts (Bricolage Grotesque, Source Serif 4)
Hosting: any static host
Project Structure
tech-pulse/
├── index.html   # markup, styles and scripts in one file
└── README.md
Run Locally
bash
git clone https://github.com/<your-username>/tech-pulse.git
cd tech-pulse
# Option 1: open index.html in a browser
# Option 2: serve it locally
python -m http.server 8000
# then visit http://localhost:8000
Deployment

GitHub Pages

Push the repository to GitHub.
Go to Settings → Pages.
Under Source, choose Deploy from a branch, then main and / (root), and save.
The site goes live at https://<your-username>.github.io/tech-pulse/.

Netlify: drag the project folder onto app.netlify.com/drop.

Vercel / Cloudflare Pages: import the repository, set no build command, and use / as the output directory.

Adding a New Source
Write a fetchYourSource() function that returns an array of { title, url, source, time, note, summary, image }.
Register it in the SOURCES object in index.html.
Add it to the fetchAll() list if you want it in the merged feed.
Limitations
Everything runs in the visitor's browser, so a source that blocks cross-origin (CORS) requests cannot be used directly.
GitHub's unauthenticated API has a low hourly rate limit.
APIs that require a secret key (for example NewsAPI or GNews) should be called through a serverless function so the key is not exposed in front-end code.
Future Improvements
Serverless proxy for key-based sources such as GNews, NewsData.io and The Guardian
Category filters (AI, security, mobile, startups)
Bookmarks and a "read later" list
Installable PWA with offline support
License

MIT. Free to use, modify and share.

Acknowledgements

Thanks to the maintainers of the Hacker News API, the Forem (DEV) API, the GitHub REST API and the Spaceflight News API for keeping their data free and open.
