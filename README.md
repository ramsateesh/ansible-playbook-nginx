# ansible-playbook-nginx

This playbook is to setup nginx as reverse proxy.  You can modify this in various ways and reuse in your projects.

## Dockerfile

You can use this docker file to mount the nginx config.  You can create further volumes for logs, sites-available, sites-enabled.

### Build the image

Use a specific version to track rather than using latest. Increment counter based on number of builds we make out of this image.
 
```
docker build -t nginx:<version>-<counter> . 
```

## Included the default config

Default config is in templates/ which can be used as reverse proxy.  It's better to inject the cert and key from a CD environment into the playbook rather than using it directly.  Sometime in futur will try to integrate with valut.

## Running the playbook

Use the below comman to run the playbook. We can use ansible-galaxy to merge the roles into the playbook, but I have left it in the roles directory.

```
ansible-playbook -s site.yml -i inventory/dev 
```

Do make sure that ansible`_user can login into inventory with id_rsa file from ansible server.
