
# Ansible Role: bash-exporter

## Description

Simple & minimalistic Prometheus exporter for bash scripts.

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `bash_exporter_version_version` | 2.0.0 | bash-exporter package version. |
| `process_exporter_web_listen_address` | "0.0.0.0:9300" | Address on which bash-exporter will listen |
| `bash_exporter_interval_int` | 300 | |
| `bash_exporter_prefix_string` | 'bash'| |
| `bash_exporter_config_dir` | /etc/bash-exporter | |
| `bash_exporter_script_dir_name` | scripts | |

## Example

```console
$ curl -s 127.1:9300/metrics | grep ^bash
bash{env="",hostname="node-1",job="job-2",verb="get"} 0.003
bash{env="",hostname="node-1",job="job-2",verb="put"} 0.13
bash{env="",hostname="node-1",job="job-2",verb="time"} 0.5
bash{env="dev",hostname="",job="job-1",verb="items"} 21
```

## Usage

```console
Usage of ./bash-exporter:
  -debug
    	Debug log level
  -interval int
    	Interval for metrics collection in seconds (default 300)
  -labels string
    	additioanal labels (default "hostname,env")
  -path string
    	path to directory with bash scripts (default "/scripts")
  -prefix string
    	Prefix for metrics (default "bash")
  -web.listen-address string
    	Address on which to expose metrics (default ":9300")
```

## Playbook

Use it in a playbook as follows:

```yaml
- hosts: all
  become: yes
  roles:
    - bash-exporter
```

## License

This project is licensed under Apache2 License. See [LICENSE](/LICENSE) for more details.

This role is inspired by https://github.com/ncabatoff/process-exporter
Bash-exporter is created by https://github.com/gree-gorey/bash-exporter
