# app.prepare

This include_role creates the user, the group and the directories for an app.

## Requirements
None

## Variables
| Name | Default | Type | Description |
| --- | --- | --- | --- |
| app_create_user | "{{ os_create_user }}" | boolean | Create non existing users and groups for the app |
| app_group | "{{ os_group }}" | str | The group name of the app user |
| app_user | "{{ os_user }}" | str | The app user name |
| app_mode | 0755 | int | The file permission mode for all files of the app |
| app_paths | [] | list[str] | The directories to be created for the app. All paths have owner={{app_user}} and group={{app_group}} and mode={{app_mode}} |

## Dependencies
None

## Minimal example

```yaml
- name: "({{ task_filename }}) Create path '/opt/app' with default os_user and os_group and permission 0755."
  include_role:
      name: app.prepare
  vars:
    app_paths:  
        - "/opt/app"
```

## Full example
```yaml
- name: "({{ task_filename }}) Create path '/opt/app' with app user and create this user."
  include_role:
      name: app.prepare
  vars:
    app_paths:  
        - "/opt/app"
    app_user: app
    app_group: app
    app_create_user: True
```

## License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Contributors
- [knelldev](https://github.com/knelldev)
- [CSteinmetz15](https://github.com/CSteinmetz15)