Ansible role: K3s
=================

Install and configure K3s.
Deploy a host as a K3s server or an agent to add to an existing cluster.

Role Variables
--------------

```
ENTRY POINT: main - Install and configure K3s

        Deploy a host as a K3s server or an agent to add to an
        existing cluster.

OPTIONS (= is mandatory):

- k3s_binary_url
        URL to download the k3s binary from
        [Default: (null)]
        type: str

- k3s_checksum
        The sha256 checksum of the binary, leave empty to get the
        checksum from k3s_checksums_url
        [Default: (null)]
        type: str

- k3s_checksums_url
        URL to download the k3s sha256 checksum file from
        [Default: (null)]
        type: str

- k3s_config
        Configuration for k3s, see
        https://rancher.com/docs/k3s/latest/en/installation/install-
        options/server-config/
        [Default: (null)]
        type: dict

- k3s_is_agent
        Set to true if the host is an agent
        [Default: False]
        type: bool

- k3s_latest_version_url
        URL for the latest version
        [Default:
        https://api.github.com/repos/k3s-io/k3s/releases/latest]
        type: str

- k3s_version
        Version to install (use "latest" for the latest version)
        [Default: latest]
        type: str

- kubernetes_ansible_requirements
        Python packages required for kubernetes ansible modules
        [Default: ['kubernetes', 'pyyaml', 'jsonpatch']]
        elements: str
        type: list

- kubernetes_kubeconfig
        Path to kubeconfig file
        [Default: /etc/rancher/k3s/k3s.yaml]
        type: str

- kubernetes_venv
        Directory for the kubernetes python virtual environment
        [Default: /opt/kubernetes/venv]
        type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/k3s,main,wandansible.k3s
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.k3s
      src: https://github.com/wandansible/k3s

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: k3s_servers
      roles:
         - role: wandansible.k3s
           become: true
