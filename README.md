If you access any of this metadata through jsdelivr, be sure to purge the file from the CDN cache after committing updates, otherwise it may take up to 7 days.

1. Go to https://www.jsdelivr.com/tools/purge
2. Enter the full path to the file, e.g. https://cdn.jsdelivr.net/gh/WazeDev/meta@main/wme-sct.json
3. Click 'Purge Now' (it may take a couple minutes for the purge to occur)

You can also use wazedev.github.io to access resources. This is likely simpler than using jsdelivr but requires using GM_xmlhttpRequest because github.io is not whitelisted in WME.

```javascript
function checkVersion() {
    GM_xmlhttpRequest({
        method: 'GET',
        url: 'https://wazedev.github.io/meta/wme-sct.json',
        headers: {
            Accept: 'application/json'
        },
        onload(response) {
            try {
                const data = JSON.parse(response.responseText);
                console.log('Available Version: ', data.version);
            } catch (err) {
                console.error('Failed to parse JSON:', err);
            }
        },
        onerror(err) {
            console.error('Request Failed:', err);
        }
    });
}
```