# `code-server` `flutter`

## Launching `code-server`
Start by cloning this repo and changing current working directory to `flutter` dir:
```bash
git clone https://github.com/mahmoudajawad/code-server-images
cd flutter
```

Make changes to `Dockerfile` concerning the extensions of your preference, by adding, updating, or removing extensions at the end of the file.

Make changes to `docker-compose.yml` according to:
1. `code-server` port: line #9.
2. `flutter-web` port: line #10.
3. `code-server` password: line #12.

Once changes are made, bring up your `docker-compose` container as following:
```bash
docker-compose up --build -d
```

Now, launch your `code-server` instance by browsing:
```
http://localhost:[CODE_SERVER_PORT]
```

## Creating or Working on Project
Once you launch `code-server` you will be greeted with the editor welcome page. You can either open the terminal to create new project, or to clone current project. Either way, you might need to do the following after creating or cloning a project to get web support for `flutter` project:
```bash
# CWD: /home/coder/project
flutter create . # Only if you cloned current project
flutter config --enable-web
```

## Debugging Project
Access `Command Palette` (Use `F1`, `Ctrl+Shift+P`, `Cmd+Shift+P`) and type and select:
```
Debug: Open launch.json
```
A context menu would appear with some options. Chose:
```
Dart & Flutter
```
You shall now get `launch.json` file opened with the following content:
```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Dart",
            "program": "bin/main.dart",
            "request": "launch",
            "type": "dart"
        }
    ]
}
```
Add the following config line to `Dart` configurations:
```json
...
            "type": "dart",
            "args": [
                "--web-port",
                "FLUTTER_WEB_PORT",
                "--web-hostname",
                "0.0.0.0"
            ]
        }
...
```
And, make sure to update `FLUTTER_WEB_PORT` with the relative value you set in `docker-compose.yml` file. You should get a dialog box from `code-server` alerting you to browse `http://0.0.0.0:FLUTTER_WEB_PORT`. Tap `Cancel` since for obvious reason browsing that URI won't do the trick. Now, using your browser browse `http://localhost:FLUTTER_WEB_PORT` and with little time of loading you should be greeted with your app interface.

## Caveats
* As of the time of writing this article, `flutter-web` is still in development and some essential areas of `flutter` APIs are not yet available for use for web development, thus, not all apps can be debugged with `code-server`.
* Debugging `Android` apps remotely using `code-server` is achievable, but, also a mind-bending game you shall play in your free time only.
* Make sure `Web Developer Tools` of your browser (, any!) are not opened when you browse to debugger web server. I've noticed in some occasions that leaving the `Tools` opened would results in the app not loading. 
