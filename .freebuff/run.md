# CreditPaper Prototype — Run Doc

## Project Type
Static HTML/CSS prototype (no build step, no package.json, no framework).

## How to Reproduce Artifacts
No compilation or dependency install needed. All files are plain HTML + CSS (`theme.css` at root, copied into `superadmin/` and `tenant-admin/`).

## How to Run the Server
Use Node's built-in `http.server` or any static file server:

```bash
# Option 1 — Node (if available)
node -e "require('http').createServer((q,r)=>{require('fs').readFile('.'+q.url.split('?')[0].replace(/\/$/,'/index.html'),(e,d)=>{r.writeHead(e?404:200,{'Content-Type':q.url.endsWith('.css')?'text/css':'text/html'});r.end(e?'Not found':d)})}).listen(58099)"

# Option 2 — Python
python -m http.server 58099
```

Port 58099 is the convention for this project. If occupied, pick another free port.

## File Structure
- `index.html` — Hub page (entry point, links to all 45 screens)
- `01-signup.html` through `24-settings-templates.html` — Main app pages
- `superadmin/` — 9 super admin pages (own `theme.css` copy)
- `tenant-admin/` — 8 tenant admin pages (own `theme.css` copy)
- `theme.css` — Shared design system (Outfit + JetBrains Mono, deep teal accent)
- `_redirects` / `_headers` — Netlify config for clean URLs
