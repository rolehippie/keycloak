# keycloak

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/keycloak) [![Testing Build](https://github.com/rolehippie/keycloak/workflows/testing/badge.svg)](https://github.com/rolehippie/keycloak/actions?query=workflow%3Atesting) [![Readme Build](https://github.com/rolehippie/keycloak/workflows/readme/badge.svg)](https://github.com/rolehippie/keycloak/actions?query=workflow%3Areadme) [![Galaxy Build](https://github.com/rolehippie/keycloak/workflows/galaxy/badge.svg)](https://github.com/rolehippie/keycloak/actions?query=workflow%3Agalaxy) [![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/keycloak)](https://github.com/rolehippie/keycloak/blob/master/LICENSE)

Ansible role to install and configure Keycloak identity service.

## Sponsor

Building and improving this Ansible role have been sponsored by my current and previous employers like **[Cloudpunks GmbH](https://cloudpunks.de)** and **[Proact Deutschland GmbH](https://www.proact.eu)**.

## Table of content

- [Default Variables](#default-variables)
  - [keycloak_cache_owners_auth_sessions_count](#keycloak_cache_owners_auth_sessions_count)
  - [keycloak_cache_owners_count](#keycloak_cache_owners_count)
  - [keycloak_database_addresses](#keycloak_database_addresses)
  - [keycloak_database_connection](#keycloak_database_connection)
  - [keycloak_database_name](#keycloak_database_name)
  - [keycloak_database_password](#keycloak_database_password)
  - [keycloak_database_schema](#keycloak_database_schema)
  - [keycloak_database_type](#keycloak_database_type)
  - [keycloak_database_username](#keycloak_database_username)
  - [keycloak_default_extensions](#keycloak_default_extensions)
  - [keycloak_default_folders](#keycloak_default_folders)
  - [keycloak_default_labels](#keycloak_default_labels)
  - [keycloak_default_publish](#keycloak_default_publish)
  - [keycloak_default_startups](#keycloak_default_startups)
  - [keycloak_default_themes](#keycloak_default_themes)
  - [keycloak_default_volumes](#keycloak_default_volumes)
  - [keycloak_extensions_path](#keycloak_extensions_path)
  - [keycloak_extra_extensions](#keycloak_extra_extensions)
  - [keycloak_extra_folders](#keycloak_extra_folders)
  - [keycloak_extra_labels](#keycloak_extra_labels)
  - [keycloak_extra_publish](#keycloak_extra_publish)
  - [keycloak_extra_startups](#keycloak_extra_startups)
  - [keycloak_extra_themes](#keycloak_extra_themes)
  - [keycloak_extra_volumes](#keycloak_extra_volumes)
  - [keycloak_group](#keycloak_group)
  - [keycloak_image](#keycloak_image)
  - [keycloak_jgroups_discovery_enabled](#keycloak_jgroups_discovery_enabled)
  - [keycloak_jgroups_discovery_external_ip](#keycloak_jgroups_discovery_external_ip)
  - [keycloak_jgroups_discovery_properties](#keycloak_jgroups_discovery_properties)
  - [keycloak_jgroups_discovery_protocol](#keycloak_jgroups_discovery_protocol)
  - [keycloak_loglevel](#keycloak_loglevel)
  - [keycloak_network](#keycloak_network)
  - [keycloak_password](#keycloak_password)
  - [keycloak_proxy_address_forwarding](#keycloak_proxy_address_forwarding)
  - [keycloak_pull_image](#keycloak_pull_image)
  - [keycloak_startups_path](#keycloak_startups_path)
  - [keycloak_themes_path](#keycloak_themes_path)
  - [keycloak_url](#keycloak_url)
  - [keycloak_user](#keycloak_user)
  - [keycloak_username](#keycloak_username)
  - [keycloak_version](#keycloak_version)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Default Variables

### keycloak_cache_owners_auth_sessions_count

Cache owners auth sessions count

#### Default value

```YAML
keycloak_cache_owners_auth_sessions_count: 1
```

### keycloak_cache_owners_count

Cache owners count

#### Default value

```YAML
keycloak_cache_owners_count: 1
```

### keycloak_database_addresses

List of database server addresses

#### Default value

```YAML
keycloak_database_addresses: []
```

#### Example usage

```YAML
keycloak_database_addresses:
  - host1
  - host2
  - host3
```

### keycloak_database_connection

Database connectiony type for clustered databases

#### Default value

```YAML
keycloak_database_connection:
```

### keycloak_database_name

Database name

#### Default value

```YAML
keycloak_database_name: keycloak
```

### keycloak_database_password

Password for database connection

#### Default value

```YAML
keycloak_database_password:
```

### keycloak_database_schema

Database schema used for PostgreSQL

#### Default value

```YAML
keycloak_database_schema:
```

### keycloak_database_type

Database driver

#### Default value

```YAML
keycloak_database_type: mariadb
```

### keycloak_database_username

Username for database connection

#### Default value

```YAML
keycloak_database_username:
```

### keycloak_default_extensions

List of default extensions

#### Default value

```YAML
keycloak_default_extensions:
  - name: keycloak-metrics-spi
    url: https://github.com/aerogear/keycloak-metrics-spi/releases/download/2.5.3/keycloak-metrics-spi-2.5.3.jar
```

#### Example usage

```YAML
keycloak_default_extensions:
  - name: example-from-url
    url: http://example.com/example.jar
  - name: example-to-remove
    state: absent
```

### keycloak_default_folders

List of default folders to create

#### Default value

```YAML
keycloak_default_folders: []
```

### keycloak_default_labels

List of default labels to assign to docker command

#### Default value

```YAML
keycloak_default_labels: []
```

### keycloak_default_publish

List of default port publishing

#### Default value

```YAML
keycloak_default_publish: []
```

#### Example usage

```YAML
keycloak_default_publish:
  - 127.0.0.1:9090:9090
```

### keycloak_default_startups

List of default startup scripts

#### Default value

```YAML
keycloak_default_startups:
  - name: keycloak
    template: keycloak.j2
```

#### Example usage

```YAML
keycloak_default_startups:
  - name: example
    content: |
      embed-server --server-config=standalone-ha.xml --std-out=echo
      batch
      run-batch
      stop-embedded-server
  - name: example-from-url
    url: http://example.com/example.yml
  - name: example-from-file
    src: path/to/file.j2
  - name: example-from-template
    template: path/to/template.j2
  - name: example-to-remove
    state: absent
```

### keycloak_default_themes

List of default themes

#### Default value

```YAML
keycloak_default_themes: []
```

#### Example usage

```YAML
keycloak_default_themes:
  - name: example-from-url
    url: http://example.com/example.tar.gz
  - name: example-to-remove
    state: absent
```

### keycloak_default_volumes

List of default volumes to mount

#### Default value

```YAML
keycloak_default_volumes: []
```

### keycloak_extensions_path

Path to store extensions

#### Default value

```YAML
keycloak_extensions_path: /usr/share/keycloak/extensions
```

### keycloak_extra_extensions

List of extra extensions

#### Default value

```YAML
keycloak_extra_extensions: []
```

#### Example usage

```YAML
keycloak_extra_extensions:
  - name: example-from-url
    url: http://example.com/example.jar
  - name: example-to-remove
    state: absent
```

### keycloak_extra_folders

List of extra folders to create

#### Default value

```YAML
keycloak_extra_folders: []
```

#### Example usage

```YAML
keycloak_extra_folders:
  - /path/to/host/folder1
  - /path/to/host/folder2
  - /path/to/host/folder3
```

### keycloak_extra_labels

List of extra labels to assign to docker command

#### Default value

```YAML
keycloak_extra_labels: []
```

### keycloak_extra_publish

List of extra port publishing

#### Default value

```YAML
keycloak_extra_publish: []
```

#### Example usage

```YAML
keycloak_extra_publish:
  - 8090:8090
  - 127.0.0.1:9000:9000
```

### keycloak_extra_startups

List of extra startup scripts

#### Default value

```YAML
keycloak_extra_startups: []
```

### keycloak_extra_themes

List of extra themes

#### Default value

```YAML
keycloak_extra_themes: []
```

#### Example usage

```YAML
keycloak_extra_themes:
  - name: example-from-url
    url: http://example.com/example.tar.gz
  - name: example-to-remove
    state: absent
```

### keycloak_extra_volumes

List of extra volumes to mount

#### Default value

```YAML
keycloak_extra_volumes: []
```

#### Example usage

```YAML
keycloak_extra_volumes:
  - /path/to/host/folder1:/path/within/container1
  - /path/to/host/folder2:/path/within/container2
  - /path/to/host/folder3:/path/within/container3
```

### keycloak_group

Group to create for container usage

#### Default value

```YAML
keycloak_group: keycloak
```

### keycloak_image

Docker image to use for deployment

#### Default value

```YAML
keycloak_image: quay.io/keycloak/keycloak:{{ keycloak_version }}
```

### keycloak_jgroups_discovery_enabled

Enable jgroups discovery

#### Default value

```YAML
keycloak_jgroups_discovery_enabled: false
```

### keycloak_jgroups_discovery_external_ip

External IP used for jgroups discovery

#### Default value

```YAML
keycloak_jgroups_discovery_external_ip:
```

### keycloak_jgroups_discovery_properties

Additional properties for jgroups discovery

#### Default value

```YAML
keycloak_jgroups_discovery_properties:
```

### keycloak_jgroups_discovery_protocol

Protocol used for jgroups discovery

#### Default value

```YAML
keycloak_jgroups_discovery_protocol:
```

### keycloak_loglevel

Logging level for the instance

#### Default value

```YAML
keycloak_loglevel: INFO
```

### keycloak_network

Optionally assign this Docker network to container

#### Default value

```YAML
keycloak_network:
```

### keycloak_password

Password for master realm access

#### Default value

```YAML
keycloak_password:
```

### keycloak_proxy_address_forwarding

Enable proxy address forwarding

#### Default value

```YAML
keycloak_proxy_address_forwarding: true
```

### keycloak_pull_image

Pull image as part of the tasks

#### Default value

```YAML
keycloak_pull_image: true
```

### keycloak_startups_path

Path to store startup scripts

#### Default value

```YAML
keycloak_startups_path: /usr/share/keycloak/startups
```

#### Example usage

```YAML
keycloak_startups_path:
  - name: example
    content: |
      embed-server --server-config=standalone-ha.xml --std-out=echo
      batch
      run-batch
      stop-embedded-server
  - name: example-from-url
    url: http://example.com/example.yml
  - name: example-from-file
    src: path/to/file.j2
  - name: example-from-template
    template: path/to/template.j2
  - name: example-to-remove
    state: absent
```

### keycloak_themes_path

Path to store themes

#### Default value

```YAML
keycloak_themes_path: /usr/share/keycloak/themes
```

### keycloak_url

URL for external access

#### Default value

```YAML
keycloak_url:
```

#### Example usage

```YAML
keycloak_url: datasource_jndi_name=java:jboss/datasources/KeycloakDS
```

### keycloak_user

User to create for container usage

#### Default value

```YAML
keycloak_user: keycloak
```

### keycloak_username

Username for master realm access

#### Default value

```YAML
keycloak_username:
```

### keycloak_version

Version of keycloak to use

#### Default value

```YAML
keycloak_version: 15.1.1
```

## Discovered Tags

**_keycloak_**


## Dependencies

- [rolehippie.docker](https://github.com/rolehippie/docker)

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)
