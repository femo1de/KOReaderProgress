## Plan: KOReader Progress SPA

Build a single-page, dependency-light site that lets users pick a folder, finds KOReader sidecar metadata for `.epub` files, parses `percent_finished`, and displays reading progress locally in the browser with a folder-picker UX suitable for GitHub Pages.

### Steps
1. Scaffold minimal HTML/CSS/JS shell in [index.html](index.html) with a progress list container and status messaging.
2. Implement folder selection in [index.html](index.html) JS using `showDirectoryPicker` with fallback to `<input webkitdirectory>` for non-supporting browsers.
3. Traverse selected folder tree to collect `.epub` files and corresponding `.sdr/metadata.<ext>.lua` sidecars, mapping by basename.
4. Parse Lua metadata files in JS to extract `percent_finished` (0–1), and derive display percent and optional status/modified fields.
5. Render progress cards/table, handle missing metadata gracefully, and add lightweight styling and instructions suitable for GitHub Pages hosting.

### Further Considerations
1. Confirm KOReader stores progress in `.sdr/metadata.<ext>.lua` (not `.srt`); proceed or adjust parsing? Option A use Lua metadata; Option B attempt SubRip `.srt`.
2. Target browsers: is Chrome/Edge acceptable for File System Access API, or should we rely on `webkitdirectory` only?
