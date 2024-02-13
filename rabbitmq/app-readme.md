# RabbitMQ

This chart is adapted from the official helm release [here](https://github.com/helm/charts/tree/master/stable/rabbitmq).

## Passwords

The cookie and password, if not set explicity at dpeloy time will be stored as a secret int he same name namespace as the deployment. The password can be recovered with the following:

    # namespace is rabbitmq
    $kubectl get secret -n rabbitmq rabbitmq-release -o jsonpath='{ .data.rabbitmq-password }' | base64 -d

## Configuration

|Value|Default|Comment
|-|-|-
|image.debug|false|Set to true if you would like to see extra information on logs
|defaultImage|true|Use default Docker images
|image.registry|docker.io|RabbitMQ Registry
|image.repository|bitnami/rabbitmq|RabbitMQ image name
|image.tag|3.7.17-debian-9-r0|RabbitMQ image tag
|rabbitmq.existingPasswordSecretEnabled|false|Use a secret to hold the RabbitMQ password
|rabbitmq.existingPasswordSecret|nil|Name of the secret holding the key name 'rabbitmq-password'
|rabbitmq.user|admin|RabbitMQ Username
|rabbitmq.password|random|description: RabbitMQ user password
|rabbitmq.existingErlangSecretEnabled|nil|Name of the secret holding the key name 'rabbitmq-erlang-cookie', otherwise the cookie will be randomly generated
|rabbitmq.existingErlangSecret|nil|Name of the secret holding the key name 'rabbitmq-erlang-cookie'
|persistence.existingClaim.enable|false|Use a manually managed PVC, set to false to let this deployment create and manage the PVC
|persistence.existingClaim||Name of the exisiting PVC, leave blank to use managed claim
|persistence.storageClass|aws-efs|storage Class of the managed PVC
|persistence.size|8Gi|description: Size of the managed PVC, e.g. 8Gi or 8Mi
|persistence.mountPath|/opt/bitnami/rabbitmq/var/lib/rabbitmq|The path the volume will be mounted at
|resources.requests.cpu|1|Amount of memory requested
|resources.requests.memory|1|Amount of cpu requestes
|resources.limits.cpu|1|Max amount of memory
|resources.limits.memory|1|Max amount of cpu