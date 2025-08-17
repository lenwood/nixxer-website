+++
date = '2025-07-07T22:56:08-05:00'
draft = false
weight = 30
title = 'Developer Documentation'
description = "Basic info about the plugin's architecture and how to expand it's capabilities."
+++

### Architecture Overview

#### Core Components

1. **Background Script** (`background.js`): The core extension engine that runs persistently in the background, handling web request interception, cookie monitoring, tracker detection across multiple platforms (Google Analytics, Facebook, Adobe, etc.), and managing the blocklist data storage with comprehensive error handling.
2. **Content Script** (`content.js`): A content script that runs on web pages to detect tracking code through DOM scanning, JavaScript global variable analysis, and zombie cookie cleanup, reporting findings back to the background script while preventing tracking persistence.
3. **Popup Interface** (`popup.html` & `popup.js`): Manages the extension's popup interface that displays real-time blocking statistics, recent tracker detections with classification labels, toggle controls, and export functionality for generating network-level blocklists.
4. **Options Page** (`options.html` & `options.js`): Handles the comprehensive settings page where users can configure detection sensitivity, manage storage limits, customize export formats, view detailed domain statistics, and import/export extension data with full error recovery.

### Manual Installation (For Developers)

**Note**: This method is for development purposes only and creates a temporary installation.

1. **Download the extension files**
   - Save all the provided files in a folder called `Nixxer`
   - Ensure the following structure:
   ```
   Nixxer/
   ├── manifest.json
   ├── background.js
   ├── content.js
   ├── popup.html
   ├── popup.js
   ├── options.html
   ├── options.js
   └── icons/
       ├── icon-16.png
       ├── icon-32.png
       ├── icon-48.png
       ├── icon-128.png
       └── icon-256.png
   ```

2. **Load in Firefox**
   - Open Firefox and navigate to `about:debugging`
   - Click "This Firefox" in the left sidebar
   - Click "Load Temporary Add-on"
   - Select the `manifest.json` file from your Nixxer folder

**Important**: Manually installed extensions are removed when Firefox is closed and must be reloaded each time.

### Adding New Tracker Support

**1. Define Detection Patterns**

```javascript
// In background.js
const NEW_TRACKER_COOKIE_PATTERNS = [
  /^_newtracker$/,
  /^nt_session_/
];

const NEW_TRACKER_REQUEST_PATTERNS = [
  /newtracker\.com\/collect/,
  /analytics\.newtracker\.net/
];
```

**2. Update Detection Functions**

```javascript
function isTrackingCookie(name, value) {
  // Add to existing checks
  const isNewTracker = NEW_TRACKER_COOKIE_PATTERNS.some(
    pattern => pattern.test(name)
  );
  
  return isNewTracker || /* existing checks */;
}
```

**3. Add to Domain Classification**

```javascript
// In determineBlockingTarget()
const THIRD_PARTY_TRACKING_DOMAINS = [
  // existing domains...
  'newtracker.com',
  'analytics.newtracker.net'
];
```

**4. Update Content Script**

```javascript
// In content.js
const COMPILED_PATTERNS = {
  newTracker: validatePatterns([
    /newTracker\.track\(/,
    /NT\.analytics\./
  ])
};
```

**5. Test Integration**

- Test on websites using the new tracker
- Verify detection in popup interface
- Confirm proper export classification
- Check performance impact
