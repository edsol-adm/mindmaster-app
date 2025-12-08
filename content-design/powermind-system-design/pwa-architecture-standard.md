# 🔒 PWA Standard - Coder Version v1.0 (Powermind)

## 1\. Scope & Paths

**Applies to:**  
All Powermind screens and games served under:

- <https://power-mind.netlify.app/powermind/>
- <https://powermind-ai.com/powermind/>

**Canonical PWA file locations (MUST):**

- Manifest:  
    /powermind/manifest.webmanifest
- Service worker:  
    /powermind/service-worker.js
- PWA icons:  
    /powermind/icons/icon-192.png  
    /powermind/icons/icon-512.png

The service worker **MUST** live in /powermind/ so its scope is /powermind/.

## 2\. Required Tags on Powermind Pages

Every Powermind HTML page (curriculum, lessons, games) MUST include:

&lt;!-- In <head&gt; -->

&lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;

&lt;link rel="manifest" href="/powermind/manifest.webmanifest"&gt;

&lt;!-- Before </body&gt; -->

&lt;script&gt;

if ('serviceWorker' in navigator) {

window.addEventListener('load', () => {

navigator.serviceWorker.register('/powermind/service-worker.js');

});

}

&lt;/script&gt;

- Paths MUST be document-relative or root-relative to /powermind/ (no full https://... URLs).
- Do NOT add a &lt;base&gt; tag.

## 3\. Manifest Requirements

Manifest file: /powermind/manifest.webmanifest

Minimum required fields:

{

"name": "Powermind",

"short_name": "Powermind",

"start_url": "/powermind/curriculum-Y01.html",

"scope": "/powermind/",

"display": "standalone",

"background_color": "#ffffff",

"theme_color": "#f97316",

"icons": \[

{

"src": "/powermind/icons/icon-192.png",

"sizes": "192x192",

"type": "image/png"

},

{

"src": "/powermind/icons/icon-512.png",

"sizes": "512x512",

"type": "image/png"

}

\]

}

Rules:

- start_url MUST remain inside /powermind/.
- scope MUST be /powermind/.
- Icons MUST exist at the specified paths and sizes.

## 4\. Service Worker: Structure & Versioning

File: /powermind/service-worker.js

### 4.1 Versioning

Top of file MUST define a cache version:

const CACHE_VERSION = 'powermind-v1';

const CACHE_NAME = \`powermind-cache-\${CACHE_VERSION}\`;

Any time cached files change significantly (new structure, assets), bump CACHE_VERSION:

const CACHE_VERSION = 'powermind-v2';

This forces an update and avoids stale cache bugs.

### 4.2 App Shell / Precache List

Precache ONLY core Unit 1 app shell + shared assets:

const PRECACHE_ASSETS = \[

'/powermind/curriculum-Y01.html',

'/powermind/lesson-screen-htmls/lesson-01.01.html',

// Unit 1 games:

// '/powermind/in-class-game-htmls/icg-01.01-game01.html',

// '/powermind/home-game-htmls/hg-01.01-game01.html',

// Shared CSS/JS:

// '/powermind/assets/common/css/main.css',

// '/powermind/assets/common/js/main.js',

// Shared images/icons:

// '/powermind/assets/common/images/powermind-logo.png',

// '/powermind/icons/icon-192.png',

// '/powermind/icons/icon-512.png'

\];

Rules:

- Do NOT blindly cache entire folders.
- Only include:
  - Curriculum + key lesson screens
  - Unit 1 game HTMLs
  - Shared CSS/JS/images used across those pages

Later units can be added explicitly when stable.

### 4.3 Install Event

self.addEventListener('install', event => {

event.waitUntil(

caches.open(CACHE_NAME).then(cache => cache.addAll(PRECACHE_ASSETS))

);

});

- MUST use PRECACHE_ASSETS from above.
- No external URLs, no absolute https://... paths.

### 4.4 Activate Event (Cleanup Old Caches)

self.addEventListener('activate', event => {

event.waitUntil(

caches.keys().then(keys =>

Promise.all(

keys

.filter(key => key.startsWith('powermind-cache-') && key !== CACHE_NAME)

.map(key => caches.delete(key))

)

)

);

});

- MUST remove old powermind-cache-\* caches when version changes.

### 4.5 Fetch Strategy

Default strategy: **cache-first, network-fallback** for GET requests within /powermind/.

self.addEventListener('fetch', event => {

const request = event.request;

// Only handle GET requests for our scope

if (request.method !== 'GET' || !request.url.includes('/powermind/')) {

return;

}

event.respondWith(

caches.match(request).then(cached => {

if (cached) return cached;

return fetch(request).then(response => {

const responseClone = response.clone();

caches.open(CACHE_NAME).then(cache => {

cache.put(request, responseClone);

});

return response;

});

})

);

});

Rules:

- Only intercept requests under /powermind/.
- Only GET requests are cached.
- Non-GET or other origins pass through to network.

## 5\. Compatibility with Navigation & Mobile Standards

Coders MUST obey existing standards:

- **Navigation Standard**
  - All navigation MUST use semantic &lt;a href="..."&gt; with document-relative paths.
  - No window.location for primary nav.
  - No &lt;base&gt; tag.
- **Mobile Standard v1.0**
  - Viewport meta tag required (already included above).
  - No overflow: hidden on &lt;body&gt; or full-page wrappers.
  - Images/canvas/video MUST be responsive (max-width: 100%; height: auto;).

PWA MUST NOT introduce:

- Absolute URLs that break offline.
- Redirect patterns that escape /powermind/ scope.

## 6\. JavaScript Rules Affecting PWA

- Do NOT globally block scrolling using event.preventDefault() on touchmove / pointermove at document/window level.
- If you must block scrolling for a specific game area, limit to the game element only.
- Games must work when loaded from cache (no reliance on window.location.origin being specific to Netlify subdomain; use relative paths).

## 7\. Testing Checklist (Coder)

Before shipping a PWA update:

- **Manifest**
  - manifest.webmanifest loads from /powermind/manifest.webmanifest
  - start_url = /powermind/curriculum-Y01.html
  - scope = /powermind/
  - Icons exist and load
- **Service Worker**
  - Registers successfully on /powermind/curriculum-Y01.html
  - New CACHE_VERSION when core assets change
  - Old caches with powermind-cache-\* are removed on activate
- **Offline behaviour**
  - With network off, previously visited Unit 1 pages still load:
    - Curriculum
    - Lesson 01.01
    - Unit 1 games
  - Navigation via anchors still works offline
  - No console errors related to SW/manifest
- **Mobile**
  - Installable on Android/Chrome (Add to Home Screen)
  - Opens full-screen (display: standalone)
  - Respects Mobile Standard (no scroll traps, responsive layout)