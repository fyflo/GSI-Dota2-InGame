# Installation & Usage

1. Add `gamestate_integration_*.cfg` file to `teamapps\common\dota 2 beta\game\dota\cfg\gamestate_integration\`.
    [Example](https://github.com/xzion/dota2-gsi/blob/master/gamestate_integration_dota2-gsi.cfg):
    
    ```
    "dota2-gsi Configuration"
    {
        "uri"               "http://localhost:3001/"
        "timeout"           "5.0"
        "buffer"            "0.1"
        "throttle"          "0.1"
        "heartbeat"         "30.0"
        "data"
        {
            "provider"      "1"
            "map"           "1"
            "player"        "1"
            "hero"          "1"
            "abilities"     "1"
            "items"         "1"
        }
        "auth"
        {
            "token"         "hello1234"
        }
    }
    
   ```
2. Run.
   ```
   1. Run bat `RUN_dota`
   2. Open http://localhost:3001.
   ```
   
3. Install [SkyWay Screenshare](https://github.com/nttcom/SkyWay-ScreenShare) browser extension on your browser.
    **Installation for Chrome**
    1. Enable Developer Mode at chrome://extensions
    2. Modify `manifest.json`.
        Example for Chrome:
        
        ```json
        {
            "name": "Dota 2 Spectating Helper screenshare enabler",
            "short_name": "D2SpectatingHelper",
            "version": "0.1",
            "manifest_version": 2,
            "description": "Allows Dota 2 Spectating Helper to use screen share",
            "icons": {
                "16": "icon16.png",
                "48": "icon48.png",
                "128": "icon128.png"
            },
            "permissions": [
                "desktopCapture",
                "tabs",
                "http://localhost:3001/*"
            ],
            "background": {
                "scripts": ["background.js"],
                "persistent": false
            },
            "content_scripts": [{
                "matches": ["http://localhost:3001/*"],
                "js": ["content.js"],
                "all_frames": true,
                "run_at": "document_end"
            }]
        }
        ```
    3. Drag and drop extension folder into chrome://extensions screen.
4. Enable "Play Sound in Desktop" and change to Borderless Window in Dota 2 settings.
5. Adjust `VIDEO_SOURCE_WIDTH`, `VIDEO_SOURCE_HEIGHT`, `VIDEO_SOURCE_FRAMERATE` in `static/index.html` depending on your video settings. (default 1366x768@60fps)

Only works for spectator, replay, or broadcaster modes.


# License
MIT

# Third-party license
dota2-gsi-fork is a fork of https://github.com/xzion/dota2-gsi, which is released under MIT License.
