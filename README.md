# librewolf-firefox-fullscreen-toolbar-fix
A simple userChrome.css tweak to stop the Firefox and LibreWolf top bar from auto-showing on hover in fullscreen mode.


# Fix: Disable Auto-Showing Top Bar in Firefox/LibreWolf Fullscreen

This repository contains a CSS tweak for **Firefox** and **LibreWolf** that prevents the toolbar (tabs and URL bar) from automatically sliding down when you hover your mouse at the top of the screen in **Fullscreen mode (F11)**.

Ideal for users seeking a distraction-free experience or those using web apps with interactive elements near the top edge.

## 🚀 How to Install

### 1. Enable Custom Stylesheets
By default, Firefox and LibreWolf ignore custom CSS files for security reasons. To enable them:
1. Open a new tab and go to `about:config`.
2. Click "Accept the Risk and Continue".
3. Search for: `toolkit.legacyUserProfileCustomizations.stylesheets`.
4. Set its value to **true**.

### 2. Locate Your Profile Folder
1. Go to `about:support` in your browser.
2. Find the **Profile Folder** section and click **Open Folder**.
3. If a folder named `chrome` does not exist, create it now.

### 3. Apply the CSS Code
1. Inside the `chrome` folder, create a text file and name it exactly `userChrome.css`.
2. Paste the following code into the file:

```css
/* ============================================================
   DISABLE FULLSCREEN TOOLBAR AUTO-SHOW
   ============================================================ */

/* 1. Kill the invisible trigger area at the top edge */
#fullscr-toggler {
    display: none !important;
}

/* 2. Physically hide the toolbar in fullscreen mode */
#navigator-toolbox[inFullscreen="true"] {
    position: relative !important;
    z-index: 0 !important;
    opacity: 0 !important;
    pointer-events: none !important;
    margin-top: -100px !important; /* Displaces it out of the viewport */
}

/* 3. Allow the bar to appear ONLY via shortcuts (Ctrl+L or Ctrl+T) */
/* This ensures you can still navigate when needed */
#navigator-toolbox[inFullscreen="true"]:focus-within {
    opacity: 1 !important;
    margin-top: 0 !important;
    pointer-events: auto !important;
}
