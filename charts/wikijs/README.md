# # wikijs

<img src="https://raw.githubusercontent.com/plcnk/charts/master/charts/wikijs/icon.svg" align="right" width="92" alt="wikijs logo">

![Version: 0.2.4](https://img.shields.io/badge/Version-0.2.4-informational?style=flat)
![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat)
![AppVersion: 2.5.305](https://img.shields.io/badge/AppVersion-2.5.305-informational?style=flat)

A modern, lightweight and powerful wiki app built on NodeJS.

**Homepage:** <https://github.com/plcnk/charts/tree/master/charts/wikijs>

**This chart is not maintained by the upstream project and any issues with the chart should be raised
[here](https://github.com/plcnk/charts/issues/new?assignees=plcnk&labels=bug&template=bug_report.yaml&name=wikijs&version=0.2.4)**

## Source Code

* <https://github.com/Requarks/wiki>

## Requirements

Kubernetes: `>=1.22.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| <https://bjw-s.github.io/helm-charts> | common | 3.3.2 |
| <https://charts.bitnami.com/bitnami> | postgresql | 16.0.5 |

## Installing the Chart

To install the chart with the release name `wikijs`

### OCI (Recommended)

```console
helm install wikijs oci://ghcr.io/plcnk/charts/wikijs
```

### Traditional

```console
helm repo add plcnk https://charts.plcnk.net
helm repo update
helm install wikijs plcnk/wikijs
```

## Uninstalling the Chart

To uninstall the `wikijs` deployment

```console
helm uninstall wikijs
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/bjw-s/helm-charts/tree/main/charts/library/common/values.yaml) from the [bjw-s common library](https://github.com/bjw-s/helm-charts/tree/main/charts/library/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install wikijs \
  --set env.TZ="America/New York" \
    plcnk/wikijs
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install wikijs plcnk/wikijs -f values.yaml
```

## Custom configuration

This chart includes a subchart for PostgreSQL, made by [Bitnami](https://github.com/bitnami/charts/tree/main/bitnami/postgresql).

This is fine for testing purposes but we strongly recommend you to use your own database for a production environment.

If you want to use your own database and disable the included PostgreSQL database, you can do so in the `values.yaml` file:

```yaml
postgresql:
  enabled: false
```

## Values

**Important**: When deploying an application Helm chart you can add more values from the bjw-s common library chart [here](https://github.com/bjw-s/helm-charts/tree/main/charts/library/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| controllers.main.containers.app.env | object | See [values.yaml](./values.yaml) | Environment variables.    The database environment variables **need** to be set if `postgresql.enabled` is set to `false` |
| controllers.main.containers.app.env.TZ | string | `"UTC"` | Set container timezone |
| controllers.main.containers.app.image.pullPolicy | string | `"IfNotPresent"` | Image pull policy |
| controllers.main.containers.app.image.repository | string | `"ghcr.io/requarks/wiki"` | Image repository |
| controllers.main.containers.app.image.tag | string | `"2.5.305"` | Image tag |
| controllers.main.containers.app.securityContext.allowPrivilegeEscalation | bool | `false` | Disable privilege escalations |
| controllers.main.containers.app.securityContext.capabilities | object | `{"drop":["ALL"]}` | Drop all capabilities |
| controllers.main.containers.app.securityContext.readOnlyRootFilesystem | bool | `true` | Mount the container's root filesystem as read-only |
| controllers.main.pod.securityContext.fsGroup | int | `65534` | Volume binds will be granted to `nobody` group |
| controllers.main.pod.securityContext.runAsGroup | int | `65534` | Run as `nobody` group |
| controllers.main.pod.securityContext.runAsNonRoot | bool | `true` | Run container as a non-root user |
| controllers.main.pod.securityContext.runAsUser | int | `65534` | Run as `nobody` user |
| controllers.main.replicas | int | `1` | Number of desired pods    **WARNING**: Set this to 1 when you first deploy Wiki.js.    You can increase the number of replicas after the initial deployment. |
| controllers.main.resources | object | `{}` | Set the resource requests / limits for the container. |
| controllers.main.type | string | `"deployment"` | Controller type |
| data | object | See [values.yaml](./values.yaml) | Configure persistent storage for Wiki.js data. |
| ingress.main | object | See [values.yaml](./values.yaml) | Enable and configure ingress settings for the chart under this key. |
| postgresql | object | See [values.yaml](./values.yaml) | Enable and configure postgresql database subchart under this key.    For more options see [postgresql chart documentation](https://github.com/bitnami/charts/tree/main/bitnami/postgresql) |
| postgresql.enabled | bool | `true` | Set this to `false` if you want to use your own database. |
| service | object | See [values.yaml](./values.yaml) | Configure the services for the chart here. |

---
Autogenerated from chart metadata using [helm-docs](https://github.com/norwoodj/helm-docs)
