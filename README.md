# chawinkn.com

Personal site of Chawin Chaisongkram (Kanoon), live at [chawinkn.com](https://chawinkn.com).

Built with [Astro](https://astro.build), React, and Tailwind CSS 4. Deployed to GitHub Pages.

## Pages

| Route    | Source                  | Content                          |
| :------- | :---------------------- | :------------------------------- |
| `/`      | `src/pages/index.astro` | Intro and weekly Unsplash photos |
| `/music` | `src/pages/music.astro` | Favorite songs and lyrics        |
| `/blogs` | `src/pages/blogs.astro` | Writing (none yet)               |

## Project Structure

```text
/
├── public/               static files, CV, favicons, music-add.html
├── src
│   ├── components/       shared Astro components
│   ├── data/music.json   song list for /music
│   ├── layouts/          Layout.astro
│   ├── pages/            routes
│   └── styles/           global.css, theme.css
└── .github/workflows/    Pages deploy
```

## Commands

Run from the project root. Requires Node >= 22.12 and [Bun](https://bun.sh).

| Command                | Action                               |
| :--------------------- | :----------------------------------- |
| `bun install`          | Install dependencies                 |
| `bun dev`              | Start dev server at `localhost:4321` |
| `bun run build`        | Build production site to `./dist/`   |
| `bun preview`          | Preview build locally                |
| `bun run format`       | Format with Prettier                 |
| `bun run format:check` | Check formatting                     |
| `bun astro check`      | Type-check                           |

Husky runs Prettier on staged files before each commit.

## Environment

| Variable              | Purpose                                                              |
| :-------------------- | :------------------------------------------------------------------- |
| `UNSPLASH_ACCESS_KEY` | Fetches weekly photos on `/`. Optional, section is empty without it. |

Set it in `.env` locally and as a repository secret for CI.

## Adding a song

Open `public/music-add.html` (served at `/music-add.html`, `noindex`) to pick lyrics, then paste the result into `src/data/music.json`:

```json
{
  "name": "Self Control",
  "artist": "Frank Ocean",
  "album": "Blonde",
  "favoriteLyrics": ["..."],
  "url": "https://www.youtube.com/watch?v=OxMLCkWm6Dc"
}
```

`album` is optional.

## Deployment

`.github/workflows/astro.yml` builds with Bun and deploys to GitHub Pages on push to `main`, on manual dispatch, and weekly on Monday at 00:10 Bangkok time so the weekly photos stay fresh.
