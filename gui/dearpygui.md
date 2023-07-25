---
description: Fast, simple UI creation framework
---

# 🐦 Dearpygui

## Installation

```bash
pip install dearpygui
```

## Example

{% code title="main.py" overflow="wrap" lineNumbers="true" %}
```python
import dearpygui.dearpygui as dpg
from callbacks import *


dpg.create_context()

# callback
def file_callback(sender, app_data):
    file_name = app_data['file_name']
    file_path = app_data['file_path_name']

    print(f"File {file_name} located at {file_path}")

# file dialog
with dpg.file_dialog(directory_selector=False, show=False, callback=file_callback, id="file_dialog_id", width=700 ,height=400):
    dpg.add_file_extension(".png", color=(0, 255, 0, 255), custom_text="[Image]")
    # only allow .png files

# Main Window    
with dpg.window(tag="main_window", label="Tutorial", width=800, height=300):
    dpg.add_button(label="Select file for upload", callback=lambda: dpg.show_item("file_dialog_id"))


dpg.create_viewport(title='File Upload', width=800, height=600)

dpg.set_exit_callback(callback=exit_callback)
dpg.set_primary_window("main_window", True)
dpg.setup_dearpygui()
dpg.show_viewport()

dpg.start_dearpygui()
dpg.destroy_context()
```
{% endcode %}

{% hint style="info" %}
`python main.py`
{% endhint %}

{% code title="callbacks.py" overflow="wrap" lineNumbers="true" %}
```python
from os import path
from shutil import copy


def move_file_to_sharepoint(sender, app_data):
    file_name = app_data['file_name']
    file_path = app_data['file_path_name']

    print(f"File {file_name} located at {file_path}")
    folder_path = "Downloads"

    folder_location = f"{folder_path }/{file_name}"
    print(f"Copying file to {folder_location}")
    copy(file_path, folder_location)

def print_callback(sender):
    print(f"Menu Item: {sender}")

def exit_callback(sender, app_data):
    print("Exiting app")
```
{% endcode %}

## Screenshots

<figure><img src="../.gitbook/assets/image (31).png" alt=""><figcaption><p>Main menu</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption><p>File browser</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption><p>File select</p></figcaption></figure>
