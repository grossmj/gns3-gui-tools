# Tools for GNS3 GUI

Tools are executables, that are called by the GNS3 GUI.
They normally use the GNS3 API (http://api.gns3.net/) to
query and/or modify the current project.

The tools are stored in the GNS3 -> tools folder.
A project must be open, to use/start them. They are
called by the GUI with the following parameters:

| No.  | Parameter                                  |
|------|--------------------------------------------|
|   1  |   GNS3 version (for compatibility checks)  |
|   2  |   Project UUID                             |
|   3+ |   List of selected items, can be empty     |

An item consists of it's UUID prefixed by `nodes/`
for node items, `text_drawings/` for text items
and `drawings/` for all other graphical elements.
Links are currently not included in the item list.

The tool can be accompanied by a JSON file, with the
same base name as the tool, but with the .json extension.

It can set the following options:

| Option        | Meaning                  | Allowed Values                    | Default   |
|---------------|--------------------------|-----------------------------------|-----------|
| name          | name of tool             | any string                        | base name |
| menu          | show in main menu        | false / true                      | true      |
| context       | show in context menu     | "disable" / "enable" / "node"     | "enable"  |
| terminal      | run in terminal window   | false / true                      | false     |
| confirm_close | confirm closing terminal | "disable" / "enable" / "on_error" | "enable"  |

With the context option "node" a tool is only shown in
the context menu, when at least one node is selected.
Instead of "disable" or "enable" the boolean values
false / true can be used.

Example of a .json file:

```
{
    "name": "Test tool",
    "menu": false,
    "context": "node",
    "terminal": true
}
```
