# ansible-role-docker-container-dependencytrack

Role to run dependencytrack in a docker container

## Table of content

- [Default Variables](#default-variables)
  - [docker_container_dependencytrack_api_base_url](#docker_container_dependencytrack_api_base_url)
  - [docker_container_dependencytrack_apiserver_comparisons](#docker_container_dependencytrack_apiserver_comparisons)
  - [docker_container_dependencytrack_apiserver_env](#docker_container_dependencytrack_apiserver_env)
  - [docker_container_dependencytrack_apiserver_image](#docker_container_dependencytrack_apiserver_image)
  - [docker_container_dependencytrack_apiserver_labels](#docker_container_dependencytrack_apiserver_labels)
  - [docker_container_dependencytrack_apiserver_name](#docker_container_dependencytrack_apiserver_name)
  - [docker_container_dependencytrack_apiserver_networks](#docker_container_dependencytrack_apiserver_networks)
  - [docker_container_dependencytrack_apiserver_ports](#docker_container_dependencytrack_apiserver_ports)
  - [docker_container_dependencytrack_apiserver_volume_dir](#docker_container_dependencytrack_apiserver_volume_dir)
  - [docker_container_dependencytrack_apiserver_volumes](#docker_container_dependencytrack_apiserver_volumes)
  - [docker_container_dependencytrack_database_name](#docker_container_dependencytrack_database_name)
  - [docker_container_dependencytrack_database_password](#docker_container_dependencytrack_database_password)
  - [docker_container_dependencytrack_database_user](#docker_container_dependencytrack_database_user)
  - [docker_container_dependencytrack_db_comparisons](#docker_container_dependencytrack_db_comparisons)
  - [docker_container_dependencytrack_db_env](#docker_container_dependencytrack_db_env)
  - [docker_container_dependencytrack_db_image](#docker_container_dependencytrack_db_image)
  - [docker_container_dependencytrack_db_labels](#docker_container_dependencytrack_db_labels)
  - [docker_container_dependencytrack_db_name](#docker_container_dependencytrack_db_name)
  - [docker_container_dependencytrack_db_networks](#docker_container_dependencytrack_db_networks)
  - [docker_container_dependencytrack_db_ports](#docker_container_dependencytrack_db_ports)
  - [docker_container_dependencytrack_db_volume_dir](#docker_container_dependencytrack_db_volume_dir)
  - [docker_container_dependencytrack_db_volumes](#docker_container_dependencytrack_db_volumes)
  - [docker_container_dependencytrack_frontend_comparisons](#docker_container_dependencytrack_frontend_comparisons)
  - [docker_container_dependencytrack_frontend_env](#docker_container_dependencytrack_frontend_env)
  - [docker_container_dependencytrack_frontend_image](#docker_container_dependencytrack_frontend_image)
  - [docker_container_dependencytrack_frontend_labels](#docker_container_dependencytrack_frontend_labels)
  - [docker_container_dependencytrack_frontend_name](#docker_container_dependencytrack_frontend_name)
  - [docker_container_dependencytrack_frontend_networks](#docker_container_dependencytrack_frontend_networks)
  - [docker_container_dependencytrack_frontend_ports](#docker_container_dependencytrack_frontend_ports)
  - [docker_container_dependencytrack_frontend_volume_dir](#docker_container_dependencytrack_frontend_volume_dir)
  - [docker_container_dependencytrack_frontend_volumes](#docker_container_dependencytrack_frontend_volumes)
  - [docker_container_dependencytrack_name](#docker_container_dependencytrack_name)
  - [docker_container_dependencytrack_restic_enable](#docker_container_dependencytrack_restic_enable)
  - [docker_container_dependencytrack_restic_retention](#docker_container_dependencytrack_restic_retention)
  - [docker_container_dependencytrack_restic_s3_bucket_name](#docker_container_dependencytrack_restic_s3_bucket_name)
  - [docker_container_dependencytrack_restic_s3_endpoint](#docker_container_dependencytrack_restic_s3_endpoint)
  - [docker_container_dependencytrack_restic_s3_repo](#docker_container_dependencytrack_restic_s3_repo)
  - [docker_container_dependencytrack_restic_s3_repo_access_key](#docker_container_dependencytrack_restic_s3_repo_access_key)
  - [docker_container_dependencytrack_restic_s3_repo_password](#docker_container_dependencytrack_restic_s3_repo_password)
  - [docker_container_dependencytrack_restic_s3_repo_secret_key](#docker_container_dependencytrack_restic_s3_repo_secret_key)
  - [docker_container_dependencytrack_restic_tag](#docker_container_dependencytrack_restic_tag)
  - [docker_container_dependencytrack_volume_dir](#docker_container_dependencytrack_volume_dir)
  - [docker_image_dependencytrack_apiserver_name](#docker_image_dependencytrack_apiserver_name)
  - [docker_image_dependencytrack_apiserver_pull](#docker_image_dependencytrack_apiserver_pull)
  - [docker_image_dependencytrack_db_name](#docker_image_dependencytrack_db_name)
  - [docker_image_dependencytrack_db_pull](#docker_image_dependencytrack_db_pull)
  - [docker_image_dependencytrack_frontend_name](#docker_image_dependencytrack_frontend_name)
  - [docker_image_dependencytrack_frontend_pull](#docker_image_dependencytrack_frontend_pull)
  - [docker_network_dependencytrack_apiserver_name](#docker_network_dependencytrack_apiserver_name)
  - [docker_network_dependencytrack_db_name](#docker_network_dependencytrack_db_name)
  - [docker_network_dependencytrack_frontend_name](#docker_network_dependencytrack_frontend_name)
  - [docker_network_dependencytrack_name](#docker_network_dependencytrack_name)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Default Variables

### docker_container_dependencytrack_api_base_url

#### Default value

```YAML
docker_container_dependencytrack_api_base_url: http://localhost:8081
```

### docker_container_dependencytrack_apiserver_comparisons

Allows to specify how properties of existing containers are compared with module options to decide whether the container should be recreated / updated or not.

#### Default value

```YAML
docker_container_dependencytrack_apiserver_comparisons:
  image: strict
  env: strict
  volumes: strict
```

### docker_container_dependencytrack_apiserver_env

Dictionery of key,value pairs for docker environment variables to configure dependencytrack.

#### Default value

```YAML
docker_container_dependencytrack_apiserver_env:
  ALPINE_DATABASE_MODE: external
  ALPINE_DATABASE_URL: jdbc:postgresql://db:5432/{{ docker_container_dependencytrack_database_name
    }}
  ALPINE_DATABASE_DRIVER: org.postgresql.Driver
  ALPINE_DATABASE_USERNAME: '{{ docker_container_dependencytrack_database_user }}'
  ALPINE_DATABASE_PASSWORD: '{{ docker_container_dependencytrack_database_password
    }}'
```

### docker_container_dependencytrack_apiserver_image

Repository path and tag used to create the container. If an image is not found or pull is true, the image will be pulled from the registry. If no tag is included, latest will be used.

#### Default value

```YAML
docker_container_dependencytrack_apiserver_image: '{{ docker_image_dependencytrack_apiserver_name
  }}'
```

### docker_container_dependencytrack_apiserver_labels

Dictionary of key value pairs for container labels.

Example:

```yaml

docker_container_dependencytrack_apiserver_labels:

traefik.enable: "true"

```

#### Default value

```YAML
docker_container_dependencytrack_apiserver_labels: {}
```

### docker_container_dependencytrack_apiserver_name

Name for the container

#### Default value

```YAML
docker_container_dependencytrack_apiserver_name: dependencytrack_apiserver
```

### docker_container_dependencytrack_apiserver_networks

List of networks the container belongs to.

#### Default value

```YAML
docker_container_dependencytrack_apiserver_networks:
  - name: '{{ docker_network_dependencytrack_apiserver_name }}'
    links:
      - '{{ docker_container_dependencytrack_db_name }}:db'
```

### docker_container_dependencytrack_apiserver_ports

List of ports to publish from the container to the host.

#### Default value

```YAML
docker_container_dependencytrack_apiserver_ports:
  - 8081:8080
```

### docker_container_dependencytrack_apiserver_volume_dir

Volume mount host directory, where Treafik config files are stored.

#### Default value

```YAML
docker_container_dependencytrack_apiserver_volume_dir: '{{ docker_container__base__volume_dir
  }}/{{ docker_container_dependencytrack_name }}'
```

### docker_container_dependencytrack_apiserver_volumes

List of volumes to mount within the container.

#### Default value

```YAML
docker_container_dependencytrack_apiserver_volumes:
  - '{{ docker_container_dependencytrack_apiserver_volume_dir }}/data:/data'
```

### docker_container_dependencytrack_database_name

Name of the database.

#### Default value

```YAML
docker_container_dependencytrack_database_name: dtrack
```

### docker_container_dependencytrack_database_password

Password of the database user.

#### Default value

```YAML
docker_container_dependencytrack_database_password: dependencytracksomethingsecret8888
```

### docker_container_dependencytrack_database_user

Name of the database user.

#### Default value

```YAML
docker_container_dependencytrack_database_user: dependencytrack
```

### docker_container_dependencytrack_db_comparisons

Allows to specify how properties of existing containers are compared with module options to decide whether the container should be recreated / updated or not.

#### Default value

```YAML
docker_container_dependencytrack_db_comparisons:
  image: strict
  env: strict
  volumes: strict
```

### docker_container_dependencytrack_db_env

Dictionery of key,value pairs for docker environment variables to configure dependencytrackdb.

#### Default value

```YAML
docker_container_dependencytrack_db_env:
  POSTGRES_USER: '{{ docker_container_dependencytrack_database_user }}'
  POSTGRES_PASSWORD: '{{ docker_container_dependencytrack_database_password }}'
  POSTGRES_DB: '{{ docker_container_dependencytrack_database_name }}'
```

### docker_container_dependencytrack_db_image

Repository path and tag used to create the container. If an image is not found or pull is true, the image will be pulled from the registry. If no tag is included, latest will be used.

#### Default value

```YAML
docker_container_dependencytrack_db_image: '{{ docker_image_dependencytrack_db_name
  }}'
```

### docker_container_dependencytrack_db_labels

Dictionary of key value pairs for container labels.

Example:

```yaml

docker_container_dependencytrack_db_labels:

traefik.enable: "true"

```

#### Default value

```YAML
docker_container_dependencytrack_db_labels: {}
```

### docker_container_dependencytrack_db_name

Name for the container

#### Default value

```YAML
docker_container_dependencytrack_db_name: dependencytrack_db
```

### docker_container_dependencytrack_db_networks

List of networks the container belongs to.

#### Default value

```YAML
docker_container_dependencytrack_db_networks:
  - name: '{{ docker_network_dependencytrack_db_name }}'
    aliases: ['{{ docker_container_dependencytrack_db_name }}', db]
```

### docker_container_dependencytrack_db_ports

List of ports to publish from the container to the host.

#### Default value

```YAML
docker_container_dependencytrack_db_ports: []
```

### docker_container_dependencytrack_db_volume_dir

Volume mount host directory, where Treafik config files are stored.

#### Default value

```YAML
docker_container_dependencytrack_db_volume_dir: '{{ docker_container__base__volume_dir
  }}/{{ docker_container_dependencytrack_name }}'
```

### docker_container_dependencytrack_db_volumes

List of volumes to mount within the container.

#### Default value

```YAML
docker_container_dependencytrack_db_volumes:
  - '{{ docker_container_dependencytrack_db_volume_dir }}/postgres:/var/lib/postgresql/data'
```

### docker_container_dependencytrack_frontend_comparisons

Allows to specify how properties of existing containers are compared with module options to decide whether the container should be recreated / updated or not.

#### Default value

```YAML
docker_container_dependencytrack_frontend_comparisons:
  image: strict
  env: strict
  volumes: strict
```

### docker_container_dependencytrack_frontend_env

Dictionery of key,value pairs for docker environment variables to configure dependencytrackdb.

#### Default value

```YAML
docker_container_dependencytrack_frontend_env:
  API_BASE_URL: '{{ docker_container_dependencytrack_api_base_url }}'
```

### docker_container_dependencytrack_frontend_image

Repository path and tag used to create the container. If an image is not found or pull is true, the image will be pulled from the registry. If no tag is included, latest will be used.

#### Default value

```YAML
docker_container_dependencytrack_frontend_image: '{{ docker_image_dependencytrack_frontend_name
  }}'
```

### docker_container_dependencytrack_frontend_labels

Dictionary of key value pairs for container labels.

Example:

```yaml

docker_container_dependencytrack_frontend_labels:

traefik.enable: "true"

```

#### Default value

```YAML
docker_container_dependencytrack_frontend_labels: {}
```

### docker_container_dependencytrack_frontend_name

Name for the container

#### Default value

```YAML
docker_container_dependencytrack_frontend_name: dependencytrack_frontend
```

### docker_container_dependencytrack_frontend_networks

List of networks the container belongs to.

#### Default value

```YAML
docker_container_dependencytrack_frontend_networks:
  - name: '{{ docker_network_dependencytrack_frontend_name }}'
```

### docker_container_dependencytrack_frontend_ports

List of ports to publish from the container to the host.

#### Default value

```YAML
docker_container_dependencytrack_frontend_ports:
  - 8080:8080
```

### docker_container_dependencytrack_frontend_volume_dir

Volume mount host directory, where Treafik config files are stored.

#### Default value

```YAML
docker_container_dependencytrack_frontend_volume_dir: '{{ docker_container__base__volume_dir
  }}/{{ docker_container_dependencytrack_name }}'
```

### docker_container_dependencytrack_frontend_volumes

List of volumes to mount within the container.

#### Default value

```YAML
docker_container_dependencytrack_frontend_volumes: []
```

### docker_container_dependencytrack_name

#### Default value

```YAML
docker_container_dependencytrack_name: dependencytrack
```

### docker_container_dependencytrack_restic_enable

Enable restic backup for the container's mounted volumes.

#### Default value

```YAML
docker_container_dependencytrack_restic_enable: false
```

### docker_container_dependencytrack_restic_retention

Retention settions for `restic forget` after the `restic backup`.

#### Default value

```YAML
docker_container_dependencytrack_restic_retention:
  keep_last: 1
  keep_daily: 7
  keep_weekly: 4
```

### docker_container_dependencytrack_restic_s3_bucket_name

Minio S3 bucket name for restic backup storage.

#### Default value

```YAML
docker_container_dependencytrack_restic_s3_bucket_name: restic-{{ docker_container_dependencytrack_name
  }}
```

### docker_container_dependencytrack_restic_s3_endpoint

Minio S3 endpoint for restic backup storage.

Example:

```yaml

docker_container__base__restic_s3_endpoint: "https://minio.{{ dns_domain }}"

docker_container_dependencytrack_restic_s3_endpoint: "{{ docker_container__base__restic_s3_endpoint }}"

```

#### Default value

```YAML
docker_container_dependencytrack_restic_s3_endpoint: '{{ docker_container__base__restic_s3_endpoint
  }}'
```

### docker_container_dependencytrack_restic_s3_repo

Minio S3 repo URL for restic backup storage.

#### Default value

```YAML
docker_container_dependencytrack_restic_s3_repo: s3:{{ docker_container_dependencytrack_restic_s3_endpoint
  }}/{{ docker_container_dependencytrack_restic_s3_bucket_name }}
```

### docker_container_dependencytrack_restic_s3_repo_access_key

Minio S3 repo access key for restic backup storage.

#### Default value

```YAML
docker_container_dependencytrack_restic_s3_repo_access_key: '{{ docker_container__base__restic_s3_repo_access_key
  }}'
```

### docker_container_dependencytrack_restic_s3_repo_password

Minio S3 repo password for restic backup storage.

#### Default value

```YAML
docker_container_dependencytrack_restic_s3_repo_password: '{{ docker_container__base__restic_s3_repo_password
  }}'
```

### docker_container_dependencytrack_restic_s3_repo_secret_key

Minio S3 repo secret key for restic backup storage.

#### Default value

```YAML
docker_container_dependencytrack_restic_s3_repo_secret_key: '{{ docker_container__base__restic_s3_repo_secret_key
  }}'
```

### docker_container_dependencytrack_restic_tag

Tag for the `restic backup` command

#### Default value

```YAML
docker_container_dependencytrack_restic_tag: '{{ docker_container_dependencytrack_name
  }}'
```

### docker_container_dependencytrack_volume_dir

#### Default value

```YAML
docker_container_dependencytrack_volume_dir: '{{ docker_container__base__volume_dir
  }}/{{ docker_container_dependencytrack_name }}'
```

### docker_image_dependencytrack_apiserver_name

Repository path and tag for the container image.

#### Default value

```YAML
docker_image_dependencytrack_apiserver_name: dependencytrack/apiserver
```

### docker_image_dependencytrack_apiserver_pull

Indicate to always pull the docker image.

#### Default value

```YAML
docker_image_dependencytrack_apiserver_pull: false
```

### docker_image_dependencytrack_db_name

Repository path and tag for the container image.

#### Default value

```YAML
docker_image_dependencytrack_db_name: postgres:14.7-alpine
```

### docker_image_dependencytrack_db_pull

Indicate to always pull the docker image.

#### Default value

```YAML
docker_image_dependencytrack_db_pull: false
```

### docker_image_dependencytrack_frontend_name

Repository path and tag for the container image.

#### Default value

```YAML
docker_image_dependencytrack_frontend_name: dependencytrack/frontend
```

### docker_image_dependencytrack_frontend_pull

Indicate to always pull the docker image.

#### Default value

```YAML
docker_image_dependencytrack_frontend_pull: false
```

### docker_network_dependencytrack_apiserver_name

Name of the docker network created for dependencytrack.

#### Default value

```YAML
docker_network_dependencytrack_apiserver_name: '{{ docker_container_dependencytrack_name
  }}_backend'
```

### docker_network_dependencytrack_db_name

Name of the docker network created for dependencytrackdb.

#### Default value

```YAML
docker_network_dependencytrack_db_name: '{{ docker_container_dependencytrack_name
  }}_backend'
```

### docker_network_dependencytrack_frontend_name

Name of the docker network created for dependencytrack_frontend.

#### Default value

```YAML
docker_network_dependencytrack_frontend_name: '{{ docker_container_dependencytrack_name
  }}_backend'
```

### docker_network_dependencytrack_name

#### Default value

```YAML
docker_network_dependencytrack_name: '{{ docker_container_dependencytrack_name }}_backend'
```

## Discovered Tags

**_docker-container-backup-all_**\
&emsp;Backup all containers' volume mounts.

**_docker-container-backup-dependencytrack_**\
&emsp;Backup dependencytrack volume mounts.

**_docker-container-backup-init-all_**\
&emsp;Run init backup task for all container.

**_docker-container-backup-init-dependencytrack_**\
&emsp;Run init backup task for dependencytrack if restic is enabled.

**_docker-container-backup-list-all_**\
&emsp;List all containers' backups.

**_docker-container-backup-list-dependencytrack_**\
&emsp;List dependencytrack backups.

**_docker-container-prereq-all_**\
&emsp;Ensure all pre-requisites are installed

**_docker-container-prereq-dependencytrack_**\
&emsp;Ensure all pre-requisites for dependencytrack are installed

**_docker-container-purge-all_**\
&emsp;Remove all containers and delete volume mounts.

**_docker-container-purge-dependencytrack_**\
&emsp;Remove dependencytrack and delete volume mounts.

**_docker-container-remove-all_**\
&emsp;Remove all containers.

**_docker-container-remove-dependencytrack_**\
&emsp;Remove dependencytrack.

**_docker-container-restore-all_**\
&emsp;Run restic restore for all restic enabled containers.

**_docker-container-restore-dependencytrack_**\
&emsp;Run restic restore for dependencytrack if restic is enabled.

**_docker-container-setup-all_**\
&emsp;Run setup task for all containers.

**_docker-container-setup-dependencytrack_**\
&emsp;Run setup task for dependencytrack.

**_never_**


## Dependencies

None.

## License

license (GPL-2.0-or-later, MIT, etc)

## Author

andif888
