<img width="1244" height="352" alt="screenshot_20260825_113051" src="https://github.com/user-attachments/assets/b717421f-f148-42d8-b120-5ec0accb3f93" />

# BBCode Editor for Godot

A simple visual BBCode editor and live preview for Godot 4.2+.

<img width="1102" height="727" alt="screenshot_20260824_182750" src="https://github.com/user-attachments/assets/8f331ceb-abb5-4381-842e-268021871d75" />


## Features

- Compact editor for BBCode-enabled `RichTextLabel` text.
- Resizable source and real-time preview panes.
- Formatting toolbar with common Godot BBCode tags.
- Inspector integration and standalone Command Palette playground. Press `Crtl + Shift + P` to open the command palette then type `bbcode`, select it to open the playground.
- Apply with `Ctrl+S`/`Cmd+S` and safe closing with `Esc`.
- Reusable editor dialog for other Godot editor plugins.

<img width="1098" height="851" alt="screenshot_20260824_174955" src="https://github.com/user-attachments/assets/24f90cec-2525-4951-b904-aff50c703ca2" />


## Installation

1. Copy `addons/bbcode_editor` into your project.
2. Open **Project > Project Settings > Plugins**.
3. Enable **BBCode Editor**.

Select a `RichTextLabel` and enable **BBCode Enabled** to use the custom text editor.

## FAQ

### How can I use the BBCode editor with a custom text field in another plugin?

Instantiate the reusable dialog, pass it the field's current text, and update the field when the dialog submits:

```gdscript
const BBCodeEditorScene = preload(
	"res://addons/bbcode_editor/ui/bbcode_editor_dialog.tscn"
)

func edit_bbcode(text_field: TextEdit) -> void:
	var dialog: BBCodeEditorDialog = BBCodeEditorScene.instantiate()
	dialog.setup(text_field.text, "Edit Text")
	dialog.text_submitted.connect(func(value: String) -> void: text_field.text = value)
	EditorInterface.get_base_control().add_child(dialog)
	dialog.open_editor()
```
