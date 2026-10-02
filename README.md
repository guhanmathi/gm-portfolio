# gm-portfolio

Personal portfolio site for **Guhan Mathiazhagan**, Senior Database Administrator (Oracle & PostgreSQL).
Served by GitHub Pages: https://guhanmathi.github.io/gm-portfolio/

Static site, no build step.

| File | Purpose |
|------|---------|
| `index.html` | Portfolio home: hero, about, expertise bento, experience, skills, certifications, contact |
| `public/gm.html` | Full resume page (print-friendly: "Print / save PDF") |
| `style.css` | Shared stylesheet for both pages |
| `assest/images/` | Logo, profile photo |

Content source: `Guhan_Mathiazhagan_Oracle_PostgreSQL_DBA.docx` (Version 5 resume).
The phone number is intentionally left off the site.

## Design (2026 refresh)

- Dark glass UI with a blue / cyan palette (`--blue #4c8dff`, `--cyan #2fd4f0`); green only for the "open to roles" status.
- Geist + Geist Mono (Google Fonts).
- Floating pill nav with scrollspy, bento expertise grid with a replication-topology diagram,
  career tenure bar, reveal-on-scroll (respects `prefers-reduced-motion`).

## Preview locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```
