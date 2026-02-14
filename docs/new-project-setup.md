Follow the [WPILib guide](https://docs.wpilib.org/en/stable/docs/software/vscode-overview/creating-robot-program.html#creating-a-new-wpilib-project) to create a new project using the following options:
1. Template
2. Java
3. Command Based
7. 1188
8. Yes


After the project is created, open the `./.vscode./settings.json`, then copy and paste the following configuration at the end of the file.

```
  "editor.formatOnSave": true,
  "java.format.settings.url": "https://raw.githubusercontent.com/google/styleguide/gh-pages/intellij-java-google-style.xml",
  "java.format.settings.profile": "GoogleStyle",
  "editor.tabSize": 2,
  "window.title": "${dirty}Reefscape"
```

For `window.title`, the `${dirty}` token shows a white dot when there are unsaved changes. Change the text `Reefscape` to the name of the current year's game (or the name of the project).