# Book Cover 3D Viewer

A browser-based 3D viewer for previewing book covers with PBR materials — foil, emboss, and spot UV finishes — under configurable lighting. Built with [Three.js](https://threejs.org/).

## What It Does

Load a `.glb` file exported from Blender and spin it under studio lighting to see how print finishes interact with light in real time. Metallic foil reflects the environment, emboss catches raked light, and spot UV shifts between gloss and matte as you rotate.

**Live:** [https://kartoonstew.github.io/book-viewer](https://kartoonstew.github.io/book-viewer)

## Usage

- **Drag and drop** a `.glb` file onto the viewer, or click **Load GLB**
- **Left-click drag** rotates the book (the object rotates, not the camera — lights stay fixed)
- **Scroll** to zoom
- **Right-click drag** to pan
- **Materials panel** controls lighting, environment, and background

## Lighting Controls

| Control | What It Does |
|---|---|
| Exposure | Overall scene brightness (tone mapping) |
| Env Intensity | How strongly the HDRI environment contributes to reflections |
| Env Rotation | Rotates the environment map — shifts where reflections land on metallic surfaces |
| Key Light Power | Intensity of the main spot light |
| Key Light Orbit/Height/Distance | Positions the spot light around the book |
| Fill / Rim / Accent | Secondary lights for balanced illumination |

## Environment Presets

Four HDRI environments from [Poly Haven](https://polyhaven.com/) (CC0, free):

- **Studio** — controlled, neutral reflections for proofing
- **Sunset** — warm, dramatic light
- **Warehouse** — high-contrast industrial reflections
- **Outdoor** — natural daylight

## Diagnostics

Click the red **Diagnose** button to inspect the full PBR material state of the loaded model — metalness, roughness, texture maps present, environment map status, and recommendations if something looks off.

## Exporting GLB from Blender

When exporting from Blender for this viewer:

1. **File → Export → glTF 2.0 (.glb)**
2. Use `.glb` format (single binary file, not `.gltf` which splits into multiple files)
3. Under export settings, ensure **Materials** is checked
4. PBR channels that carry over: Base Color, Metallic, Roughness, Normal
5. The viewer applies its own lighting and environment — you don't need to export lights or cameras

## Tech Stack

- [Three.js](https://threejs.org/) r162 (ES modules via unpkg CDN)
- [Poly Haven](https://polyhaven.com/) 4K HDRIs (loaded at runtime)
- Zero build step — single HTML file, no npm/webpack/bundler
- Hosted free on GitHub Pages

## Part Of

This viewer is one component of the **Book Cover Rendering Engine** — a pipeline that takes InDesign print specifications (IDML files with foil, emboss, and spot UV layers) and renders photorealistic 3D book mockups using Blender as a headless backend. The viewer provides the interactive preview and shareable output layer.

## License

Viewer code: MIT. HDRI environments: CC0 (Poly Haven).
