# Frontify Desktop App

## Customer Configuration

In order to restrict the some user actions a custom config file has to be created in:

- Windows: `%APPDATA%\Roaming\Frontify Companion\app-config.json`
- macOS: `~/Library/Application Support/Frontify Companion/app-config.json`

Example file:

``` json
{
    "domain": "weare.frontify.com",
    "brandId": 1,
    "autoUpdateEnabled": false,
    "guidelineFilter": {
        "include": [1, 2, 3]
    },
    "documentfilter": {
        "exclude": [5, 6, 7]
    }
}
```

### Options

- `domain` (optional)
    - Description: This is the domain the user should connect to, without "http://" or "https://". If this option is set, the user won't be able to connect to another Frontify instance.
    - Default: `undefined`
    - Type: String
- `brandId` (optional)
    - Description: This is the brand's id the user will connect to. If this option is set, the user won't be able to change the brand.
    - Default: `undefined`
    - Type: Number
- `autoUpdateEnabled` (optional)
    - Description: With this option enabled, the user is allowed to download and install updates on his own (requires administrator rights on Windows depending on the installation location).
    - Default: `true`
    - Type: Boolean
- `autostartApp` (optional)
    - Description: By default the app will register itself as an autostart application. If you don't want the app to automatically start when the user logs in you can set this to `false`. If this option is not speficied or if it's set to `true` the user can enable/disable autostart by herself/himself.
    - Default: `undefined`
    - Type: Boolean
- `guidelineFilter` (optional)
    - Description: This object defines a filter to include or exclude guidlines in the search scope dropdown menu.
    - Default: `undefined`
    - Type: Object
    - `include` (optional)
        - Description: An array of guidline ids which should be included in the dropdown when changing the search scope.
        - Default: `undefined`
        - Type: Array\<Number>
    - `exclude` (optional)
        - Description: An array of guideline ids which should be excluded from the dropdown when chaning the search scope. **This option will be ingored when `include` is specified.**
        - Default: `undefined`
        - Type: Array\<Number>
- `documentFilter` (optional)
    - Description: This object defines a filter to include or exclude documents in the search scope dropdown menu.
    - Default: `undefined`
    - Type: Object
    - `include` (optional)
        - Description: An array of document ids which should be included in the dropdown when changing the search scope.
        - Default: `undefined`
        - Type: Array\<Number>
    - `exclude` (optional)
        - Description: An array of document ids which should be excluded from the dropdown when chaning the search scope. **This option will be ingored when `include` is specified.**
        - Default: `undefined`
        - Type: Array\<Number>
- `projectFilter` (optional)
    - Description: This object defines a filter to include or exclude documents connected to a specific project in the search scope dropdown menu.
    - Default: `undefined`
    - Type: Object
    - `include` (optional)
        - Description: An array of project ids which should be included in the dropdown when changing the search scope.
        - Default: `undefined`
        - Type: Array\<Number>
    - `exclude` (optional)
        - Description: An array of project ids which should be excluded from the dropdown when chaning the search scope. **This option will be ingored when `include` is specified.**
        - Default: `undefined`
        - Type: Array\<Number>

