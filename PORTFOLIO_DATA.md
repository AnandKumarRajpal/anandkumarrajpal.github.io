# Portfolio data

Edit `src/data/portfolio.json` to update projects, experience, achievements, and research. No code changes needed—just edit the file and rebuild/redeploy.

## Structure

- **projects**: `title`, `link` (GitHub URL or null), `description` (array of strings), `skills` (array of strings)
- **experience**: `id` (number, for sort order), `name`, `path_to_icon` (e.g. `"assets/logo.svg"`), `position`, `from`, `to`, `description` (array of strings, or see WorkExperience.vue for the nested format)
- **achievements**: `title`, `description`, `linkTitle`, `link` (or null), `iconLink` (e.g. `"assets/award.svg"`), `noFilter` (boolean, for light-mode icon)
- **research**: `id`, `Type` (`"Peer-Reviewed Conference Paper"` or `"Poster"`), `Authors` (array), `Title`, `Year`, `Venue`, `PDF` (filename under `public/papers/` or null), `Video`, `DOI` (or null)

Put PDFs in `public/papers/` and reference by filename in the `PDF` field.
