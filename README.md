# tasks
This extension loads VSCode tasks into status bar.

## Options
You can hide some tasks with the following options directly in `tasks.json`:

Value of the `hide` attribute can be hardcoded:

```json
"label": "Test",
"options": {
  "statusbar": {
    "hide" : "true"
  }
}
```

Also, value of the `hide` attribute can be evaluated automatically using predefined variables and input variables. The evaluation is done during loading/reloading of tasks status bar. If the final value of `hide` attribute is `true`, then the task is hidden from status bar; otherwise, the task is shown. This approach can be efficiently combined with methods of dynamic evaluation of input variables, such as [Tasks Shell Input](https://marketplace.visualstudio.com/items?itemName=augustocdias.tasks-shell-input) to test necessary conditions, check environment variables, run scripts etc.

```json
"label": "Test",
"options": {
  "statusbar": {
    "hide": "${input:isTaskShouldBeHidden}"
  }
}
```

You can set the label of the statusbar:

```json
"label": "Test",
"options": {
  "statusbar": {
    "label" : "ts"
  }
}
```

You can embed icons in the text by leveraging the syntax: `$(icon-name)`. More details in [icons-in-labels](https://code.visualstudio.com/api/references/icons-in-labels) and [octicons](https://octicons.github.com)

```json
"label": "Test",
"options": {
  "statusbar": {
    "label" : "$(beaker) ts"
  }
}
```

You can set the foreground color of the statusbar:

```json
"label": "Test",
"options": {
  "statusbar": {
    "color" : "#22C1D6"
  }
}
```

You can set the tooltip of the statusbar:

```json
"label": "Test",
"options": {
  "statusbar": {
    "detail" : "my test"
  }
}
```

You can enable statusbar items based on the file in the active editor using the `filePattern` attribute, causing the statusbar item to be hidden when the active file does not match the specified pattern. If the `filePattern` attribute is not provided, the statusbar item will not be hidden based on the active file. Also, if it is provided but is invalid or causes an error during validation, the statusbar item will not be displayed. (Note that `filePattern` only applies to statusbar items that have not been otherwise effectively set as hidden through `tasks.json` or `settings.json`).

For instance, the following would only display the "Test" button when a filename beginning with `test_` is the active editor:

```json
"label": "Test",
"options": {
  "statusbar": {
    "filePattern" : "test_.*"
  }
}
```
