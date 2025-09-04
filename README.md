# IMT - Interactive Map Tiles

A simple, lightweight web application for viewing raster tile services in an interactive map interface.

## Purpose

IMT (Interactive Map Tiles) is a minimalist web-based map viewer that allows users to display and explore raster tile layers from any TileJSON-compatible source. It provides a clean, fullscreen map interface perfect for visualizing geographic data, satellite imagery, or custom map tiles.

## Demo

- **Live Demo**: [https://hfu.github.io/imt/](https://hfu.github.io/imt/)
- **Demo with Custom Data**: [https://hfu.github.io/imt/?tilejson=https://tunnel.optgeo.org/martin/HOT-Jamata-Cockle-Bay-Freetown](https://hfu.github.io/imt/?tilejson=https://tunnel.optgeo.org/martin/HOT-Jamata-Cockle-Bay-Freetown)
- **Demo with Location Hash**: [https://hfu.github.io/imt/?tilejson=https://tunnel.optgeo.org/martin/maxar-2020-freetown#13.87/8.46905/-13.24495](https://hfu.github.io/imt/?tilejson=https://tunnel.optgeo.org/martin/maxar-2020-freetown#13.87/8.46905/-13.24495)
- **Demo with Specific Location**: [https://hfu.github.io/imt/#17.55/8.488833/-13.271331](https://hfu.github.io/imt/#17.55/8.488833/-13.271331)
- **3D Demo with Custom Data**: [https://hfu.github.io/imt/3d.html?tilejson=https://tunnel.optgeo.org/martin/maxar-2020-freetown#13.87/8.46905/-13.24495/165.9/53](https://hfu.github.io/imt/3d.html?tilejson=https://tunnel.optgeo.org/martin/maxar-2020-freetown#13.87/8.46905/-13.24495/165.9/53)
- **3D Demo with Location**: [https://hfu.github.io/imt/3d.html#17.55/8.488833/-13.271331/0/53](https://hfu.github.io/imt/3d.html#17.55/8.488833/-13.271331/0/53)

## Usage

### Basic Usage
Simply navigate to the application URL to view the default map layer (HOT-Jamata-Cockle-Bay-Freetown).

### Custom Tile Sources
To display your own raster tiles, add the `tilejson` parameter to the URL:

```
https://hfu.github.io/imt/?tilejson=YOUR_TILEJSON_URL
```

**Example:**
```
https://hfu.github.io/imt/?tilejson=https://tunnel.optgeo.org/martin/HOT-Jamata-Cockle-Bay-Freetown
```

### Map Interaction
- **Pan**: Click and drag to move around the map
- **Zoom**: Use mouse wheel or zoom controls
- **Permalink**: The map state (zoom level and center) is preserved in the URL hash for easy sharing

## Technical Details

### Technology Stack
- **MapLibre GL JS** (v5.0.0): Modern, performant map rendering library
- **Vanilla JavaScript**: No additional frameworks or dependencies
- **CSS3**: Simple, responsive fullscreen layout

### How It Works
1. The application reads the `tilejson` URL parameter from the query string
2. If no parameter is provided, it defaults to the HOT Freetown dataset
3. MapLibre GL JS creates a map instance with a raster source pointing to the TileJSON URL
4. The map fills the entire viewport with navigation controls and hash-based URL updates

### Code Structure
The entire application is contained in a single HTML file (`docs/index.html`) with:
- **HTML**: Basic document structure with a map container
- **CSS**: Fullscreen map styling
- **JavaScript**: Map initialization and URL parameter handling

### Data Format
IMT works with any raster tile service that provides a TileJSON endpoint. The TileJSON specification defines how tile URLs, zoom levels, and other metadata are structured.

## Examples

### Default Dataset
The default view shows HOT (Humanitarian OpenStreetMap Team) data for the Jamata Cockle Bay area in Freetown, Sierra Leone.

### Custom Usage
You can use IMT to display:
- Satellite imagery
- Custom map tiles
- Research datasets
- Historical maps
- Any raster tile service with TileJSON support

## License

This project is released under the [CC0 1.0 Universal](LICENSE) license, making it freely available for any use without restrictions.

## Contributing

This is a simple, focused tool designed to remain lightweight. The codebase is intentionally minimal to ensure easy understanding and modification.