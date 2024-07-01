# Domain Proxy Service

## Parameters

### Domain Proxy Service Parameters

| Name                       | Description                                                             | Value              |
| -------------------------- | ----------------------------------------------------------------------- | ------------------ |
| `config.replicaCount`      | The amount of containers to run                                         | `1`                |
| `config.type`              | The type of service to create                                           | `LoadBalancer`     |
| `config.appPort`           | The port to expose the service and application on                       | `8000`             |
| `config.nodePort`          | The nodePort to use if the the service type is LoadBalancer or NodePort | `30345`            |
| `config.commonAnnotations` | The annotations to set on the Domain Proxy Service application          | `{}`               |
| `config.debug`             | Whether or not to enable debug mode for the application                 | `False`            |
| `config.logLevel`          | The log level to use for the application                                | `DEBUG`            |
| `config.api.host`          | The hostname of the API Gateway service                                 | `apigateway`       |
| `config.api.port`          | The port of the API Gateway service                                     | `8000`             |
| `config.kas.host`          | The hostname of the Keep Alive service                                  | `keepaliveservice` |
| `config.kas.port`          | The port of the Keep Alive service                                      | `8000`             |

### Domain Proxy Service Image Parameters

| Name                | Description                                                | Value                                 |
| ------------------- | ---------------------------------------------------------- | ------------------------------------- |
| `image.repository`  | The repository to use for the Domain Proxy Service image   | `ghcr.io/cdecatapult/reason-domproxy` |
| `image.pullPolicy`  | The pull policy to use for the Domain Proxy Service image  | `Always`                              |
| `image.tag`         | The tag to use for the Domain Proxy Service image          | `v0.1.4`                              |
| `image.pullSecrets` | The pull secrets to use for the Domain Proxy Service image | `["reason"]`                          |

### Domain Proxy Service Ingress parameters

| Name                        | Description                                                                    | Value      |
| --------------------------- | ------------------------------------------------------------------------------ | ---------- |
| `ingress.enabled`           | Whether or not to enable the ingress for the Domain Proxy Service application  | `true`     |
| `ingress.annotations`       | The annotations to set on the ingress for the Domain Proxy Service application | `{}`       |
| `ingress.ingressClassName`  | The ingress class to use for the Domain Proxy Service application              | `""`       |
| `ingress.hostname`          | The hostname to use for the Domain Proxy Service application                   | `""`       |
| `ingress.paths`             | The paths to use for the Domain Proxy Service application                      |            |
| `ingress.paths[0].path`     | The path to use for the Domain Proxy Service application                       | `/api/dps` |
| `ingress.paths[0].pathType` | The path type to use for the Domain Proxy Service application                  | `Prefix`   |

### Domain Proxy Service ServiceAccount parameters

| Name                         | Description                                                                     | Value   |
| ---------------------------- | ------------------------------------------------------------------------------- | ------- |
| `serviceAccount.create`      | Whether or not to create a service account for the Domain Proxy Service service | `false` |
| `serviceAccount.annotations` | The annotations to use for the Domain Proxy Service service account             | `{}`    |
| `serviceAccount.name`        | The name of the service account to use for the Domain Proxy Service service     | `""`    |

### Domain Proxy Service PostgreSQL parameters

| Name                                          | Description                                                                           | Value         |
| --------------------------------------------- | ------------------------------------------------------------------------------------- | ------------- |
| `postgresql.enabled`                          | Whether or not to enable the PostgreSQL SubChart for the Domain Proxy Service service | `true`        |
| `postgresql.primary.service.ports.postgresql` | The port to expose the PostgreSQL database service on                                 | `5432`        |
| `postgresql.auth.username`                    | The username to use for the PostgreSQL database                                       | `dpsuser`     |
| `postgresql.auth.password`                    | The password to use for the PostgreSQL database                                       | `dpspassword` |
| `postgresql.auth.database`                    | The name of the database to use for the PostgreSQL database                           | `domproxy`    |
