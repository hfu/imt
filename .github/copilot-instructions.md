# IMT (Interactive Map Tiles)
IMT is a lightweight, static HTML web application that displays interactive raster map tiles using MapLibre GL. The application allows viewing custom tile sources via URL parameters and is designed for simple deployment and usage.

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively

### Bootstrap and serve the application:
- No build process required - this is a static HTML application
- **Python HTTP server (recommended)**: `cd /home/runner/work/imt/imt && python3 -m http.server 8000`
  - Access at: `http://localhost:8000/docs/index.html`
  - Response time: ~0.004s
  - NEVER CANCEL: Server starts instantly, always runs indefinitely until stopped
- **PHP built-in server**: `cd /home/runner/work/imt/imt && php -S localhost:8080`
  - Access at: `http://localhost:8080/docs/index.html`
  - NEVER CANCEL: Server starts in ~1 second, runs indefinitely until stopped
- **NPX serve**: `cd /home/runner/work/imt/imt && npx serve docs/ -p 8001`
  - Access at: `http://localhost:8001/`
  - NEVER CANCEL: First run takes ~30 seconds to install dependencies, subsequent runs are ~3 seconds
  - Will install serve@14.2.4 on first use

### Dependencies and external resources:
- **External dependencies**: MapLibre GL 5.0.0 from unpkg.com CDN
  - CSS: `https://unpkg.com/maplibre-gl@5.0.0/dist/maplibre-gl.css`
  - JS: `https://unpkg.com/maplibre-gl@5.0.0/dist/maplibre-gl.js`
  - **NOTE**: Network access may be limited in some environments - external resources may not load
- **Default tile source**: `https://tunnel.optgeo.org/martin/HOT-Jamata-Cockle-Bay-Freetown`
  - **NOTE**: External tile sources may not be accessible in restricted network environments

### GitHub Pages deployment:
- **AUTOMATIC**: GitHub Pages is already configured and active
- **Deployment source**: `docs/` directory on main branch
- **Access URL**: Available via GitHub Pages after pushing to main branch
- **Workflow**: `pages-build-deployment` workflow handles automatic deployment
- **NEVER CANCEL**: Pages deployment takes 1-3 minutes. Set timeout to 5+ minutes.

## Validation

### Manual validation requirements:
- **ALWAYS test the application after making changes** by serving it locally and accessing in browser
- **Complete validation scenario**: 
  1. Start HTTP server using any of the methods above
  2. Open `http://localhost:[port]/docs/index.html` (or appropriate URL)
  3. Verify the map container loads (HTML structure)
  4. **NOTE**: Full map functionality requires external network access for MapLibre GL and tile sources
  5. Test custom tile source: `?tilejson=https://example.com/tiles.json` parameter
- **File validation**: 
  - HTML file size should be ~1283 bytes
  - Verify HTML structure contains MapLibre GL script tags and map container div
- **ALWAYS validate serving methods work** before documenting any changes

### Testing without network access:
- **HTML structure validation**: `curl -s http://localhost:8000/docs/index.html | head -10`
- **Response time check**: `curl -o /dev/null -s -w "Response time: %{time_total}s\n" http://localhost:8000/docs/index.html`
- **HTTP status verification**: `curl -I http://localhost:8000/docs/index.html`

## Common Tasks

### Repository structure:
```
/home/runner/work/imt/imt/
├── .git/
├── .github/
│   └── copilot-instructions.md
├── docs/
│   └── index.html                 # Main application file
└── LICENSE                        # CC0 1.0 Universal license
```

### File operations:
- **Copy files**: `cp docs/index.html docs/backup.html`
- **Edit HTML**: Use `str_replace_editor` tool to modify `docs/index.html`
- **Validate changes**: Always serve locally and test after modifications

### Customizing tile sources:
- **Query parameter method**: Add `?tilejson=YOUR_TILEJSON_URL` to any URL
- **Code modification**: Edit line 20 in `docs/index.html`:
  ```javascript
  const tilejsonUrl = getQueryParam('tilejson') || 'YOUR_DEFAULT_URL';
  ```
- **ALWAYS test custom tile sources** by serving locally and accessing with parameter

### Available tools and versions:
- **Python**: 3.12.3 (HTTP server available)
- **Node.js**: v20.19.4
- **NPM**: 10.8.2  
- **PHP**: 8.3.6 (built-in server available)

### Git operations:
- **Check status**: `git --no-pager status`
- **View history**: `git --no-pager log --oneline -10`
- **Current branch**: `copilot/fix-3`
- **Remote**: `origin https://github.com/hfu/imt`

## Timing Expectations

- **File operations**: Instant (copying, editing)
- **Python HTTP server start**: Instant
- **PHP server start**: ~1 second  
- **NPX serve first run**: ~30 seconds (package installation)
- **NPX serve subsequent runs**: ~3 seconds
- **HTTP response time**: ~0.004 seconds
- **GitHub Pages deployment**: 1-3 minutes (NEVER CANCEL)

## External Dependencies Note

**CRITICAL**: This application relies on external CDN resources that may not be accessible in restricted network environments:
- MapLibre GL CSS and JavaScript from unpkg.com
- Default tile source from tunnel.optgeo.org
- In network-restricted environments, you can still validate HTML structure and serving functionality
- For full map functionality testing, ensure external network access is available

## Quick Reference Commands

**Start serving (choose one):**
```bash
# Python (recommended)
cd /home/runner/work/imt/imt && python3 -m http.server 8000

# PHP  
cd /home/runner/work/imt/imt && php -S localhost:8080

# NPX serve
cd /home/runner/work/imt/imt && npx serve docs/ -p 8001
```

**Validate application:**
```bash
# Test HTTP response
curl -I http://localhost:8000/docs/index.html

# Check HTML content
curl -s http://localhost:8000/docs/index.html | head -10
```

**File operations:**
```bash
# View HTML structure  
str_replace_editor view /home/runner/work/imt/imt/docs/index.html

# Edit tile source
str_replace_editor str_replace /home/runner/work/imt/imt/docs/index.html "old_url" "new_url"
```