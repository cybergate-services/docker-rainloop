# docker-rainloop

This container provides Rainloop web mail as an alternative to Roundcube and Sogo web mail in OpenEMAIL. This container is based on [hardware/rainloop](https://github.com/hardware/rainloop)

# docker-compose

To use this container in OpenEMAIL add the following codes to `docker-conmpose.yml` in your **OpenEMAIL** installation.

```
rainloop-openemail:
  image: hardware/rainloop
  container_name: rainloop
  links:
    - mysql:mysql
  volumes:
    - ./data/rainloop:/rainloop/data
  depends_on:
    - mysql
  dns:
    - ${IPV4_NETWORK:-172.22.1}.254
  networks:
    openemail-network:
      aliases:
        - rainloop
```
