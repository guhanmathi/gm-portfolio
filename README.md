# gm-portfolio

Personal portfolio site for **Guhan Mathiazhagan**, Senior Database Administrator (Oracle & PostgreSQL).
Served by GitHub Pages: https://guhanmathi.github.io/gm-portfolio/

Static site, no build step.

| File | Purpose |
|------|---------|
| `index.html` | The site: hero, about, expertise bento, experience, skills, certifications, contact |
| `style.css` | Stylesheet (bump the `?v=` query in `index.html` when it changes, to beat the Pages cache) |
| `assest/images/` | Logo, profile photo |

Content source: `Guhan_Mathiazhagan_Oracle_PostgreSQL_DBA.docx` (Version 5 resume).
The site is built from the resume, but there is deliberately no resume page or download, and no
phone number.

## Design (2026 refresh)

- Dark glass UI with a blue / cyan palette (`--blue #4c8dff`, `--cyan #2fd4f0`).
- No job-seeking / availability wording on the site (kept private).
- Geist + Geist Mono (Google Fonts).
- Floating pill nav with scrollspy, bento expertise grid with a replication-topology diagram,
  career tenure bar, reveal-on-scroll (respects `prefers-reduced-motion`).

## Preview locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```
