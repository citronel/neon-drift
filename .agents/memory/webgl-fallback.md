---
name: WebGL fallback
description: Browser preview environments can lack a usable WebGL context even when Three.js is installed.
---

Three.js game surfaces should probe for WebGL before constructing `WebGLRenderer` and provide a lightweight playable fallback instead of allowing renderer creation to crash the React tree.

**Why:** The Replit preview browser can run without a WebGL context, while real phones and desktop browsers may support it. A graceful fallback keeps preview and low-power devices usable and avoids treating an environment limitation as an app error.

**How to apply:** Keep the full Three.js path for capable browsers, but render a small 2D canvas scene with the same controls and core game loop when the probe fails. Avoid invoking `WebGLRenderer` when the probe already reports no support.