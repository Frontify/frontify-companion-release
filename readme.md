# Frontify Desktop App

## Installation options

### Windows

If you want to run an automated installation with a Script it's recommended to run the installer with the "silent" option. Additionally you can specify the installation location.

Here is an example (Powershell):

```
PS> .\Frontify-Setup-2.0.0.exe /S /D="C:\Program Files\Frontify"
```

| Commandline option | Description                                                             |
| ------------------ | ----------------------------------------------------------------------- |
| `/S`               | Runs the installer in the background without any installation dialog    |
| `/D="<PATH>"`      | Specifies the installation location (requires Administrator privilege). |

### CLI arguments

| CLI argument        | Description                                                                                                                                                                 | Example                       |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------- |
| `domain`            | This is the domain the user should connect to, without "http://" or "https://". If this option is set, the user won't be able to connect to another Frontify instance.      | `--domain=brand.frontify.com` |
| `brandId`           | This is the domain the user should connect to, without "http://" or "https://". If this option is set, the user won't be able to connect to another Frontify instance.      | `--brandId=1`                 |
| `autoUpdateEnabled` | With this option enabled, the user is allowed to download and install updates on his own (requires administrator rights on Windows depending on the installation location). | `--autoUpdateEnabled=false`   |
| `autostartApp`      | By default the app will register itself as an autostart application. If you don't want the app to automatically start when the user logs in you can set this to `false`.    | `--autostartApp=false`        |
| `includeGuidelines` | An array of guidline ids which should be included in the dropdown when changing the search scope.                                                                           | `--includeGuidelines=1,2,3`   |
| `includeDocuments`  | An array of guideline ids which should be excluded from the dropdown when chaning the search scope. This option will be ingored when `includeGuidelines` is specified.      | `--includeDocuments=1,2,3`    |
| `includeProjects`   | An array of document ids which should be included in the dropdown when changing the search scope.                                                                           | `--includeProjects=1,2,3`     |
| `excludeGuidelines` | An array of document ids which should be excluded from the dropdown when chaning the search scope. This option will be ingored when `includeDocuments` is specified.        | `--excludeGuidelines=1,2,3`   |
| `excludeDocuments`  | An array of project ids which should be included in the dropdown when changing the search scope.                                                                            | `--excludeGuidelines=1,2,3`   |
| `excludeProjects`   | An array of project ids which should be excluded from the dropdown when chaning the search scope. This option will be ingored when `includeProjects` is specified.          | `--excludeProjects=1,2,3`     |

If you're using Frontify for Desktop v1.x.x please check out our [legacy customization options](legacy-customization-options.md).
