# Role Name

This role installs the [clamav-unofficial-sigs](https://github.com/extremeshok/clamav-unofficial-sigs) script and configures it as well as the systemd timer.


## Requirements

The original repo/script is supported [by many distributions](https://github.com/extremeshok/clamav-unofficial-sigs/tree/master/config), e.g.
- Debian
- Ubuntu
- Raspbian
- CentOS
- ArchLinux
- OpenSuse
- Solaris
- FreeBSD
- OpenBSD
- pfsense

This role is tested on *Debian 9 (stretch)* but should work on any `systemd` compatible distribution.
Note that dependencies are only installed on `apt`-like systems.


## Role Variables

| Name                                    | Required/Default   | Description                                                                                                                                        |
|-----------------------------------------|:------------------:|----------------------------------------------------------------------------------------------------------------------------------------------------|
| `global_cache_dir`                      | :heavy_check_mark: | A directory on the Ansible Controller where the repo will be cloned to for caching purposes.                                                       |
| `clamav_unofficial_sigs_frequency`      | `hourly`           | Frequency of updates. See [systemd.time](https://www.freedesktop.org/software/systemd/man/systemd.time.html#Calendar%20Events) for allowed values. |
| `clamav_unofficial_sigs_config`         | :heavy_check_mark: | Dict keys and string values. You should include `user_configuration_complete`=`yes` for the script to work.                                        |
| `clamav_unofficial_sigs_additional_dbs` | `[]`               | List of additional database sources, e.g. `ftp`, `http`, `rsync` addresses.                                                                        |
| `clamav_unofficial_sigs_os`             | `debian`           | Set which [OS setting file](https://github.com/extremeshok/clamav-unofficial-sigs/tree/master/config) should be used.                              |


## Example

```yml
clamav_unofficial_sigs_config:
  malwarepatrol_receipt_code: 123456
  malwarepatrol_list: clamav_basic
  securiteinfo_authorisation_signature: 654321
  clamd_socket: /run/clamav/clamd.sock
  downloader_ignore_ssl: "no"
  user_configuration_complete: "yes"
```


## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Author Information

- [Michel Weitbrecht (SlothOfAnarchy)](https://github.com/SlothOfAnarchy) _michel.weitbrecht@stuvus.uni-stuttgart.de_
