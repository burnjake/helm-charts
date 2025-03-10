# Hawkbit update server

## Introduction

[Eclipse hawkBit™](https://www.eclipse.org/hawkbit/) is a domain independent back-end framework for rolling out software updates to constrained edge devices as well as more powerful controllers and gateways connected to IP based networking infrastructure.

This chart uses hawkbit/hawkbit-update-server container to run Hawkbit update server inside Kubernetes.

## Prerequisites

-   Has been tested on Kubernetes 1.11+

## Installing the Chart

To install the chart with the release name `hawkbit-update-server`, run the following command:

```bash
$ helm install kiwigrid/hawkbit-update-server --name hawkbit-update-server
```

## Uninstalling the Chart

To uninstall/delete the `hawkbit-update-server` deployment:

```bash
$ helm delete hawkbit-update-server
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

> **Tip**: To completely remove the release, run `helm delete --purge hawkbit-update-server`

## Configuration

The following table lists the configurable parameters of the hawkbit-update-server chart and their default values.

| Parameter                                  | Description                               | Default                            |
| ------------------------------------------ | ----------------------------------------- | ---------------------------------- |
| `image.repository`                         | Docker image repo                         | `hawkbit/hawkbit-update-server`    |
| `image.tag`                                | Docker image                              | `0.3.0M3-mysql`                    |
| `image.pullPolicy`                         | Docker image pull policy                  | `IfNotPresent`                     |
| `image.pullSecrets`                        | Docker image pull secrets                 | `{}`                               |
| `service.type`                             | Service type                              | `ClusterIP`                        |
| `service.port`                             | Service port of hawkbit-update-server UI  | `80`                               |
| `resources`                                | Resource limits for the pod               | `{}`                               |
| `ingress.enabled`                          | Ingress enabled                           | `false`                            |
| `ingress.annotations`                      | Ingress annotations                       | `{}`                               |
| `ingress.path`                             | Ingress path                              | `/`                                |
| `ingress.hosts`                            | Ingress hosts                             | `[]`                               |
| `ingress.tls`                              | Ingress TLS                               | `[]`                               |
| `resources`                                | Resources                                 | `{}`                               |
| `nodeSelector`                             | NodeSelector                              | `{}`                               |
| `tolerations`                              | Tolerations                               | `[]`                               |
| `affinity`                                 | Affinity                                  | `{}`                               |
| `useMysql`                                 | use MySQL dependency chart                | `true`                             |
| `useRabbitmq`                              | user Rabbitmq dependency chart            | `true`                             |
| `livenessProbe.initialDelaySeconds`        | livenessProbe initialDelaySeconds         | `240`                              |
| `livenessProbe.timeoutSeconds`             | livenessProbe timeoutSeconds              | `5`                                |
| `readinessProbe.initialDelaySeconds`       | readinessProbe timeoutSeconds             | `120`                              |
| `readinessProbe.timeoutSeconds`            | readinessProbe timeoutSeconds             | `5`                                |
| `security.passwordEncoder`                 | Spring Password encoder                   | `"{noop}"`                         |
| `env.springDatasourceHost`                 | MySQL host                                | `"hawkbit-update-server-mysql"`    |
| `env.springDatasourceUsername`             | MySQL user                                | `"hawkbit"`                        |
| `env.springDatasourcePassword`             | MySQL pass                                | `"hawkbit"`                        |
| `env.springDatasourceDb`                   | MySQL db                                  | `"hawkbit"`                        |
| `env.springRabbitmqHost`                   | RabbitMq host                             | `"hawkbit-update-server-rabbitmq"` |
| `env.springRabbitmqUsername`               | RabbitMq user                             | `"hawkbit"`                        |
| `env.springRabbitmqPassword`               | RabbitMq pass                             | `"hawkbit"`                        |
| `env.springSecurityUserName`               | Hawkbit user                              | `"admin"`                          |
| `env.springSecurityUserPassword`           | Hawkbit pass                              | `""`                               |
| `oidc.enabled`                             | enable OpenID Connect authentication      | `false`                            |
| `oidc.clientId`                            | OpenID Connect client ID                  | `""`                               |
| `oidc.clientSecret`                        | OpenID Connect client secret              | `""`                               |
| `oidc.issuerUri`                           | OpenID Connect issuer URI                 | `""`                               |
| `oidc.authorizationUri`                    | OpenID Connect authorization URI          | `""`                               |
| `oidc.tokenUri`                            | OpenID Connect token URI                  | `""`                               |
| `oidc.userInfoUri`                         | OpenID Connect user info URI              | `""`                               |
| `oidc.jwkSetUri`                           | OpenID Connect JWK set URI                | `""`                               |
| `extraEnv`                                 | Optional environment variables            | `{}`                               |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example:

```bash
$ helm install --name hawkbit-update-server --set ingress.enabled=false kiwigrid/hawkbit-update-server
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart.
