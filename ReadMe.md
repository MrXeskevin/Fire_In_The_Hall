# Neon Trigger AR 

A browser-based Augmented Reality shooter that turns your hand into a controller. Built in a single HTML file using **Three.js** for rendering and **MediaPipe Hands** for computer vision.

## Gameplay
* **The Gesture:** Make a "Finger Gun" with your hand .
* **Aim:** Point your index finger at the screen to control the crosshair.
* **Shoot:** Close your thumb (like a hammer striking) to fire.
* **The Goal:** Destroy the red discs before they fly past you. The game features **Magnetic Aim Assist**, so if your crosshair turns red, you are locked on!

##  How to Run
Because this uses the webcam, modern browsers require a secure context (HTTPS) or localhost.

1.  **Download:** Save the code as `index.html`.
2.  **Local Server (Recommended):**
    * If you have Python installed: run `python -m http.server` in the folder.
    * If you have VS Code: use the "Live Server" extension.
3.  **Direct File Open:** Some browsers (Chrome) allow camera access via `file://`, but a local server is more reliable.
4.  **Permissions:** Allow Camera access when prompted.

## Technical Implementation
This project was built to solve specific stability issues common in WebAR development:

* **Zero-Dependency Setup:** Everything is contained in one file; no `npm install` required.
* **Crash-Safe Version Locking:** Explicitly locks MediaPipe WASM binaries to version `0.4.1646424915` to prevent the common "WASM Version Mismatch" crash.
* **Async Loading:** Implements a loading overlay to ensure heavy AI models are fully initialized before the game loop starts.
* **Decoupled Loops:** * **Rendering:** Runs at 60 FPS (Three.js `requestAnimationFrame`).
    * **AI Detection:** Runs throttled (~20 FPS) to prevent UI freezing on lower-end devices.

##  License
Open Source. Feel free to modify and use for your own AR experiments.
