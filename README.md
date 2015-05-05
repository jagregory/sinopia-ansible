# Sinopia NPM registry

Setup and configure the [Sinopia NPM registry](https://github.com/rlidwka/sinopia).

## Requirements

NodeJS is required, tested with `nodesource.node`.

## Role Variables

`sinopia_version`: The version of Sinopia to install (default: `1.2.2`)

`sinopia_config`: The Sinopia configuration directory (default: `/etc/sinopia`)

`sinopia_storage`: Data storage location for Sinopia (default: `/var/sinopia`)

`sinopia_host`: The host which Sinopia will listen on (default: `localhost`)

`sinopia_port`: Port on which Sinopia will listen (default: `4873`)

`sinopia_manage_users`: Allow Ansible to manage the Sinopia users through the `sinopia_htpasswd` setting (default: `no`)

`sinopia_max_users`: Number of users allowed to register (default: `.inf`)

`sinopia_htpasswd`: The htpasswd file which Sinopia uses to store users. This key can either be the string contents of the htpasswd file, or key/value pairs of username/password. To manage Sinopia users with this setting, make sure `sinopia_manage_users` is set to `yes`.

```yaml
user1: {SHA}b12edasfa...
user2: {SHA}b12edasfa...
```

`sinopia_user`: The Linux user and group which Sinopia will run under (default: `sinopia`)

`sinopia_uplinks`: The remote NPM registries to link to (default: public npm)

```yaml
- name: npmjs
  url: https://registry.npmjs.org/
```

`sinopia_packages`: List of packages patterns for managing access (default: authenticated publish, anonymous access)

```yaml
- name: '*'
  access: '$anonymous'
  publish: '$authenticated'
```

## Vagrant

To launch a local Sinopia exposed on port `4873` run:

    ansible-galaxy install -r requirements.txt
    vagrant up

