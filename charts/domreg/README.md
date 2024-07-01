# Domain Registration Service

## Parameters

### Domain Registration Service Parameters

| Name                       | Description                                                             | Value             |
| -------------------------- | ----------------------------------------------------------------------- | ----------------- |
| `config.replicaCount`      | The amount of containers to run                                         | `1`               |
| `config.type`              | The type of service to create                                           | `LoadBalancer`    |
| `config.appPort`           | The port to expose the service and application on                       | `8000`            |
| `config.nodePort`          | The nodePort to use if the the service type is LoadBalancer or NodePort | `30342`           |
| `config.commonAnnotations` | The annotations to set on the Domain Registration Service application   | `{}`              |
| `config.debug`             | Whether or not to enable debug mode for the application                 | `False`           |
| `config.logLevel`          | The log level to use for the application                                | `DEBUG`           |
| `config.gui.host`          | The hostname of the GUI service                                         | `portal`          |
| `config.gui.port`          | The port of the GUI service                                             | `8000`            |
| `config.uas.host`          | The hostname of the User Authentication service                         | `userauthservice` |
| `config.uas.port`          | The port of the User Authentication service                             | `8000`            |

### Domain Registration Service Image Parameters

| Name                | Description                                                       | Value                               |
| ------------------- | ----------------------------------------------------------------- | ----------------------------------- |
| `image.repository`  | The repository to use for the Domain Registration Service image   | `ghcr.io/cdecatapult/reason-domreg` |
| `image.pullPolicy`  | The pull policy to use for the Domain Registration Service image  | `Always`                            |
| `image.tag`         | The tag to use for the Domain Registration Service image          | `0.1.7`                             |
| `image.pullSecrets` | The pull secrets to use for the Domain Registration Service image | `["reason"]`                        |

### Domain Registration Service Ingress parameters

| Name                        | Description                                                                           | Value      |
| --------------------------- | ------------------------------------------------------------------------------------- | ---------- |
| `ingress.enabled`           | Whether or not to enable the ingress for the Domain Registration Service application  | `true`     |
| `ingress.annotations`       | The annotations to set on the ingress for the Domain Registration Service application | `{}`       |
| `ingress.ingressClassName`  | The ingress class to use for the Domain Registration Service application              | `""`       |
| `ingress.hostname`          | The hostname to use for the Domain Registration Service application                   | `""`       |
| `ingress.paths`             | The paths to use for the Domain Registration Service application                      |            |
| `ingress.paths[0].path`     | The path to use for the Domain Registration Service application                       | `/api/drs` |
| `ingress.paths[0].pathType` | The path type to use for the Domain Registration Service application                  | `Prefix`   |

### Domain Registration Service ServiceAccount parameters

| Name                         | Description                                                                            | Value   |
| ---------------------------- | -------------------------------------------------------------------------------------- | ------- |
| `serviceAccount.create`      | Whether or not to create a service account for the Domain Registration Service service | `false` |
| `serviceAccount.annotations` | The annotations to use for the Domain Registration Service service account             | `{}`    |
| `serviceAccount.name`        | The name of the service account to use for the Domain Registration Service service     | `""`    |

### Domain Registration Service PostgreSQL parameters

| Name                                          | Description                                                                                  | Value         |
| --------------------------------------------- | -------------------------------------------------------------------------------------------- | ------------- |
| `postgresql.enabled`                          | Whether or not to enable the PostgreSQL SubChart for the Domain Registration Service service | `true`        |
| `postgresql.primary.service.ports.postgresql` | The port to expose the PostgreSQL database service on                                        | `5432`        |
| `postgresql.auth.username`                    | The username to use for the PostgreSQL database                                              | `drsuser`     |
| `postgresql.auth.password`                    | The password to use for the PostgreSQL database                                              | `drspassword` |
| `postgresql.auth.database`                    | The name of the database to use for the PostgreSQL database                                  | `domreg`      |
