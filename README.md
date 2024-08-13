<p align="center">
    <img width="200px" height=auto src="https://helm.sh/img/helm.svg" />
</p>

<p align="center">
    <a href="https://github.com/minicloudlabs/helm-charts/blob/main/LICENSE"><img src="https://img.shields.io/github/license/minicloudlabs/helm-charts" /></a>
    <a href="https://artifacthub.io/packages/search?repo=plcnk"><img src="https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/plcnk" /></a>
    <a href="https://github.com/plcnk/charts/actions/workflows/release.yaml"><img src="https://github.com/plcnk/charts/actions/workflows/release.yaml/badge.svg" /></a>
</p>

# plcnk's Helm Charts

Charts for deploying applications on [Kubernetes](https://kubernetes.io/) using [Helm](https://helm.sh/).

The code in this repository is provided as-is with no warranties.

## Usage

[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs/) to get started.

Once Helm is set up properly, add the repo as follows:

```console
helm repo add plcnk https://charts.plcnk.net
helm repo update
```

You can then run `helm search repo plcnk` to see the charts.

## Available charts

| Chart | Description |
| ----- | ----------- |
| [IT-Tools <img src='https://raw.githubusercontent.com/plcnk/charts/master/charts/it-tools/icon.svg' alt='it-tools icon' width='18px' align='right' loading='lazy'>](charts/it-tools/) | Collection of handy online tools for developers, with great UX. |

## License

This project is licensed under the [MIT License](https://github.com/plcnk/charts/blob/master/LICENSE).
