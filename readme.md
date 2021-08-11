# Frontify Desktop App

## Installation options

If you want to run an automated installation with a Script it's recommended to run the installer with the "silent" option. Additionally you can specify the installation location.

Here is an example using Powershell:

```
PS> .\Frontify-Setup-2.0.0.exe /S /D="C:\Program Files\Frontify"
```

| Commandline option | Description                                                             |
| ------------------ | ----------------------------------------------------------------------- |
| `/S`               | Runs the installer in the background without any installation dialog    |
| `/D="<PATH>"`      | Specifies the installation location (requires Administrator privilege). |

## Deployment in an enterprise Windows environment

Here is a short guide how we would recommend deploying the app in your enterprise environment.

1. [Download](https://github.com/frontify/frontify-companion-release/releases/latest) the latest `.exe` or `.msi` installer.
2. Install the application on the user's machine using a Powershell or Batch script in silent mode:
   ```
   PS> .\Frontify-Setup-2.0.0.exe /S /D="C:\Program Files\Frontify"
   ```
3. The installer will most likely create a shortcut on the desktop and in the Windows start menu. As we assume that your employees are not familiar with the name "Frontify" we recommend removing these shortcuts and creating custom shortcuts.
4. Create a new shortcut in `C:\ProgramData\Microsoft\Windows\Start Menu\Programs`. The target of the shortcut should point to `C:\Program Files\Frontify\Frontify.exe`. This shortcut will show up in the user's start menu. Change the name of the shortcut to something your employees will recognize as your brand portal.
5. We recommend adding a predefined domain so your employees don't have to type in your brand domain manually. To do so change the shortcut's target to this: `C:\Program Files\Frontify\Frontify.exe --domain=<YOUR_DOMAIN>`
6. As we assume that your average Windows user doesn't have privileges to install applications on the computer we recommend turning off the auto update mechanism. Change the shortcut's target to `C:\Program Files\Frontify\Frontify.exe --domain=<YOUR_DOMAIN> --autoUpdateEnabled=false`
7. Check the full documentation on all available [CLI arguments](#cli-arguments) which can be used to control the app's behavior.
8. If possible you can also change the shortcut's icon to your brand logo so your users will recognize the app.

## CLI arguments

These CLI arguments can be used to control the app's behavior or restrict some user actions.

Example:

```
PS> .\Frontify.exe --domain=brand.frontify.com --autoUpdateEnabled=false
```

| CLI argument        | Description                                                                                                                                                                 | Example                       |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------- |
| `domain`            | This is the domain the user should connect to, without "http://" or "https://". If this option is set, the user won't be able to connect to another Frontify instance.      | `--domain=brand.frontify.com` |
| `brandId`           | This is the id of the brand that you want the user to connect to. If this option is specified the user won't be able to choose another brand in your environment.           | `--brandId=1`                 |
| `autoUpdateEnabled` | With this option enabled, the user is allowed to download and install updates on his own (requires administrator rights on Windows depending on the installation location). | `--autoUpdateEnabled=false`   |
| `autostartApp`      | By default the app will register itself as an autostart application. If you don't want the app to automatically start when the user logs in you can set this to `false`.    | `--autostartApp=false`        |
| `includeGuidelines` | An array of guidline ids which should be included in the dropdown when changing the search scope.                                                                           | `--includeGuidelines=1,2,3`   |
| `includeDocuments`  | An array of guideline ids which should be excluded from the dropdown when chaning the search scope. This option will be ingored when `includeGuidelines` is specified.      | `--includeDocuments=1,2,3`    |
| `includeProjects`   | An array of document ids which should be included in the dropdown when changing the search scope.                                                                           | `--includeProjects=1,2,3`     |
| `excludeGuidelines` | An array of document ids which should be excluded from the dropdown when chaning the search scope. This option will be ingored when `includeDocuments` is specified.        | `--excludeGuidelines=1,2,3`   |
| `excludeDocuments`  | An array of project ids which should be included in the dropdown when changing the search scope.                                                                            | `--excludeDocuments=1,2,3`    |
| `excludeProjects`   | An array of project ids which should be excluded from the dropdown when chaning the search scope. This option will be ingored when `includeProjects` is specified.          | `--excludeProjects=1,2,3`     |

If you're using Frontify for Desktop v1.x.x please check out our [legacy customization options](legacy-customization-options.md).

## Windows Registry Entries

The app will add entries in the following Windows registry paths depending on if you install the app for just the current user or for all users.

| Installation location | Registry Path                                                      |
| --------------------- | ------------------------------------------------------------------ |
| Current user          | `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`  |
| All users             | `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run` |
