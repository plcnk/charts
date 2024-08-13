# IT-Tools

Helm chart for deploying [it-tools](https://it-tools.tech/).

it-tools is a collection of handy online tools for developers, with great UX.

> [!NOTE]
> This chart is not maintained by the original author of it-tools and any problems with this chart should be submitted [here](https://github.com/plcnk/charts/issues/new).

## Source code

* <https://github.com/CorentinTh/it-tools>

## Installing the Chart

To install the chart with the release name `it-tools`

### OCI (Recommended)

```console
helm install it-tools oci://ghcr.io/plcnk/charts/it-tools
```

### Traditional

```console
helm repo add plcnk https://charts.plcnk.net
helm repo update
helm install it-tools plcnk/it-tools
```

## Uninstalling the Chart

To uninstall the `it-tools` deployment

```console
helm uninstall it-tools
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Parameters

### Global parameters

| Name               | Description                                    | Value |
| ------------------ | ---------------------------------------------- | ----- |
| `replicaCount`     | Number of replicas for the it-tools Deployment | `1`   |
| `imagePullSecrets` | Docker registry pull secrets                   | `[]`  |
| `nameOverride`     | Name override                                  | `""`  |
| `fullnameOverride` | Full name override                             | `""`  |
| `podAnnotations`   | Additional annotations for the Pod resource    | `{}`  |
| `podLabels`        | Additional labels for the Pod resource         | `{}`  |
| `nodeSelector`     | Node labels for pod assignment                 | `{}`  |
| `tolerations`      | Tolerations for pod assignment                 | `[]`  |
| `affinity`         | Affinity for pod assignment                    | `{}`  |

### Image parameters

| Name               | Description                                                   | Value                         |
| ------------------ | ------------------------------------------------------------- | ----------------------------- |
| `image.repository` | Docker image repository                                       | `ghcr.io/corentinth/it-tools` |
| `image.pullPolicy` | Docker image pull policy                                      | `IfNotPresent`                |
| `image.tag`        | Overrides the image tag whose default is the chart appVersion | `""`                          |

### Service account parameters

| Name                         | Description                                                                                                            | Value   |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ------- |
| `serviceAccount.create`      | Specifies whether a service account should be created                                                                  | `false` |
| `serviceAccount.automount`   | Automatically mount a ServiceAccount's API credentials?                                                                | `true`  |
| `serviceAccount.annotations` | Additional annotations for the ServiceAccount resource                                                                 | `{}`    |
| `serviceAccount.name`        | The name of the service account to use. If not set and create is true, a name is generated using the fullname template | `""`    |

### Security context parameters

| Name                                       | Description                               | Value            |
| ------------------------------------------ | ----------------------------------------- | ---------------- |
| `securityContext.capabilities.drop`        | Capabilities to drop                      | `["ALL"]`        |
| `securityContext.readOnlyRootFilesystem`   | If root filesystem should be read-only    | `true`           |
| `securityContext.runAsNonRoot`             | If pod should be run as non-root          | `true`           |
| `securityContext.runAsUser`                | User to run pod as                        | `10099`          |
| `securityContext.runAsGroup`               | Group to run pod as                       | `10099`          |
| `securityContext.allowPrivilegeEscalation` | If privilege escalation should be allowed | `false`          |
| `securityContext.seccompProfile.type`      | seccomp profile type                      | `RuntimeDefault` |

### Service parameters

| Name           | Description            | Value       |
| -------------- | ---------------------- | ----------- |
| `service.type` | Service type to create | `ClusterIP` |
| `service.port` | Service port to use    | `80`        |

### Ingress parameters

| Name                  | Description                                                              | Value   |
| --------------------- | ------------------------------------------------------------------------ | ------- |
| `ingress.enabled`     | Enable ingress record generation                                         | `false` |
| `ingress.className`   | IngressClass that will be be used to implement the Ingress               | `""`    |
| `ingress.annotations` | Additional annotations for the Ingress resource                          | `{}`    |
| `ingress.hosts`       | An array with hostname(s) to be covered with the ingress record          | `[]`    |
| `ingress.tls`         | TLS configuration for hostname(s) to be covered with this ingress record | `[]`    |

### Resources parameters

| Name        | Description          | Value |
| ----------- | -------------------- | ----- |
| `resources` | Kubernetes resources | `{}`  |

### Autoscaling parameters

| Name                                            | Description                          | Value   |
| ----------------------------------------------- | ------------------------------------ | ------- |
| `autoscaling.enabled`                           | Enable Horizontal POD autoscaling    | `false` |
| `autoscaling.minReplicas`                       | Minimum number of replicas           | `1`     |
| `autoscaling.maxReplicas`                       | Maximum number of replicas           | `100`   |
| `autoscaling.targetCPUUtilizationPercentage`    | Target CPU utilization percentage    | `80`    |
| `autoscaling.targetMemoryUtilizationPercentage` | Target Memory utilization percentage | `80`    |
