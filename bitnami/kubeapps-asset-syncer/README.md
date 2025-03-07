# Kubeapps Asset Syncer packaged by Bitnami

## What is Kubeapps Asset Syncer?

> Kubeapps Asset Syncer is one of the main components of Kubeapps, a Web-based application deployment and management tool for Kubernetes clusters. It scans a chart repository and populates its metadata.

[Overview of Kubeapps Asset Syncer](https://github.com/vmware-tanzu/kubeapps)



## TL;DR

```console
$ docker run --name kubeapps-asset-syncer bitnami/kubeapps-asset-syncer:latest
```

## Why use Bitnami Images?

* Bitnami closely tracks upstream source changes and promptly publishes new versions of this image using our automated systems.
* With Bitnami images the latest bug fixes and features are available as soon as possible.
* Bitnami containers, virtual machines and cloud images use the same components and configuration approach - making it easy to switch between formats based on your project needs.

## How to deploy Kubeapps Asset Syncer in Kubernetes?

Deploying Bitnami applications as Helm Charts is the easiest way to get started with our applications on Kubernetes. Read more about the installation in the [Bitnami Kubeapps Chart GitHub repository](https://github.com/bitnami/charts/tree/master/bitnami/kubeapps).

## Why use a non-root container?

Non-root container images add an extra layer of security and are generally recommended for production environments. However, because they run as a non-root user, privileged tasks are typically off-limits. Learn more about non-root containers [in our docs](https://docs.bitnami.com/tutorials/work-with-non-root-containers/).

## Supported tags and respective `Dockerfile` links

Learn more about the Bitnami tagging policy and the difference between rolling tags and immutable tags [in our documentation page](https://docs.bitnami.com/tutorials/understand-rolling-tags-containers/).


* [`2`, `2-scratch`, `2.5.1`, `2.5.1-scratch-r2`, `latest` (2/scratch/Dockerfile)](https://github.com/bitnami/containers/blob/main/bitnami/kubeapps-asset-syncer/2/scratch/Dockerfile)

## Configuration

For further documentation, please check [here](https://github.com/vmware-tanzu/kubeapps/tree/master/cmd/asset-syncer).

## Contributing

We'd love for you to contribute to this container. You can request new features by creating an [issue](https://github.com/bitnami/containers/issues), or submit a [pull request](https://github.com/bitnami/containers/pulls) with your contribution.

## Issues

If you encountered a problem running this container, you can file an [issue](https://github.com/bitnami/containers/issues/new/choose). For us to provide better support, be sure to fill the issue template.

## License

Copyright &copy; 2022 Bitnami

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
