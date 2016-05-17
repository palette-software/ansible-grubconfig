# ansible-grubconfig
Ansible module for editing GRUB config files  (/etc/grub.conf)


## Synopsis

Adds and removes kernel flags from /etc/grub.conf in a repeatable way.

## Requirements (on host that executes module)

* python

## Options

| parameter | required | choices            | default        | comments                                                                                                                                                                                |
|-----------|----------|--------------------|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| file      | no       |                    | /etc/grub.conf | The grub.conf file to edit                                                                                                                                                              |
| flag      | yes      |                    |                | The actual kernel flag. Can either be KEY or KEY=VALUE formatted.                                                                                                                       |
| state     | no       | <ul><li>present</li><li>absent</li></ul> | present        | Whether to add/set (<code>present<code>) or remove (<code>absent</code>) the flag                                                                                                                    |
| value     | no       |                    |                | If the flag to be changed is of the KEY=VALUE type, this parameter specifies the value for the flag (if the flag is already set with a different value, it overrides the existing flag) |

## Examples

```yaml

- name: Add 'transparent_hugepages=never' to the kernel flags
  grubconfig: flag=transparent_hugepages value=never

- name: Remove the 'rhgb' flag from the kernel flags
  grubconfig: flag=rhgb state=absent

- name: Add the 'quiet' flag
  grubconfig: flag=quiet state=present
```
