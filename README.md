# ThreeFrame · Cover Studio

Turn portrait videos and images into a landscape cover, entirely in your browser. No installation, account, build step, or media upload is required.

The interface opens in **English** by default. Use the language menu in the header to switch to **简体中文**. Your browser remembers the preference when local storage is available. Switching languages preserves imported media, panel order, crop positions, and your title. Native video-player controls and download dialogs follow your browser or operating-system language.

[中文使用说明](使用说明.md)

## Run locally

Open `index.html` in a recent Chrome or Edge browser. On Windows, you can also double-click `Open Cover Studio.cmd`. The HTML file is self-contained, with no external libraries or network dependencies.

1. Import one video to automatically pick frames at 18%, 50%, and 82% of its duration. With multiple videos, the app picks the midpoint of each of the first three videos; if only two are available, it reuses the second video for the third panel.
2. Alternatively, import images. The first three fill the panels. Extra images stay available in each panel's dropdown. With fewer than three images, remaining empty panels reuse the last imported image.
3. Select a panel, drag the video timeline to preview frames live, then choose **Capture to panel**. Fast scrubbing prioritizes your latest target. You can also enter seconds or move by 0.1 seconds.
4. Reorder panels, adjust horizontal / vertical crop focus, choose a background, and optionally add a title.
5. Choose an output size and export a full-resolution JPG or PNG.

## Cover sizes

| Aspect ratio | Output sizes |
| --- | --- |
| 16:9 | 1280×720, 1920×1080, 2560×1440, 3840×2160 |
| 4:3 | 1200×900, 1600×1200, 2048×1536 |

Three 9:16 images side by side have a combined ratio of 27:16. **Fill** crops slightly from the top and bottom for 16:9, and from the sides for 4:3. Adjust focus to keep the subject in view, or choose **Fit** with a solid or blurred background to preserve the full image. The preview uses the same aspect ratio as the exported cover.

## Host on GitHub Pages

This is a static HTML app. GitHub Pages serves the page; frame decoding, compositing, and export happen on the visitor's device. There is no server process to run and no API key to configure.

When publishing, use **the contents of this `cover-studio` folder** as the repository root. This keeps unrelated workspace videos out of the repository and puts `index.html` at the publishing root.

1. Push this folder's contents to the target repository.
2. In the repository's **Settings → Pages**, choose **Deploy from a branch**.
3. Select the branch containing `index.html`, choose **/(root)**, and save.
4. Wait for deployment and open the URL provided by GitHub Pages.

The included `.nojekyll` file disables Jekyll processing. Assets do not use absolute site paths, so both user sites and repository project sites are supported.

See GitHub's official instructions for [publishing sources](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site) and [creating a Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site).

## Privacy and limitations

- Selected videos and images remain in browser memory. The app does not send them to a server or include analytics. Hosting providers still handle normal requests for the webpage.
- Only the interface language preference is stored. Reloading or closing the page clears imported media and unsaved edits. Export before reloading.
- Recommended input: MP4 (H.264), JPG, PNG, or WebP. HEVC, MOV, and other formats depend on browser and device decoder support.
- Automatic selection uses timestamps, without content recognition or quality scoring.
- Moving by 0.1 seconds is a time adjustment, not frame-accurate editing.
- Extracted video images are capped at 2160 pixels on their longest edge. A larger output does not create additional source detail.
- Processing many large files can use substantial memory. Work in smaller groups when needed.
- The app makes one three-panel cover at a time; folder-wide batch export is not included.

## Verification

JavaScript syntax and application logic have been checked with simulated DOM and media events. Real-browser visual rendering and codec behavior still need verification before public release.
