# Kubernetes Event Exporter packaged by Bitnami

## What is Kubernetes Event Exporter?

> Kubernetes Event Exporter makes it easy to export Kubernetes events to other tools, thereby enabling better event observability, custom alerts and aggregation.

[Overview of Kubernetes Event Exporter](https://github.com/resmoio/kubernetes-event-exporter)

Trademarks: This software listing is packaged by Bitnami. The respective trademarks mentioned in the offering are owned by the respective companies, and use of them does not imply any affiliation or endorsement.

## TL;DR

```console
$ docker run --name kubernetes-event-exporter bitnami/kubernetes-event-exporter:latest
```

### Docker Compose

```console
$ curl -sSL https://raw.githubusercontent.com/bitnami/containers/main/bitnami/kubernetes-event-exporter/docker-compose.yml > docker-compose.yml
$ docker-compose up -d
```

## Why use Bitnami Images?

* Bitnami closely tracks upstream source changes and promptly publishes new versions of this image using our automated systems.
* With Bitnami images the latest bug fixes and features are available as soon as possible.
* Bitnami containers, virtual machines and cloud images use the same components and configuration approach - making it easy to switch between formats based on your project needs.

## How to deploy Kubernetes Event Exporter in Kubernetes?

Deploying Bitnami applications as Helm Charts is the easiest way to get started with our applications on Kubernetes. Read more about the installation in the [Bitnami Kubernetes Event Exporter Chart GitHub repository](https://github.com/bitnami/charts/tree/master/bitnami/kubernetes-event-exporter).

## Why use a non-root container?

Non-root container images add an extra layer of security and are generally recommended for production environments. However, because they run as a non-root user, privileged tasks are typically off-limits. Learn more about non-root containers [in our docs](https://docs.bitnami.com/tutorials/work-with-non-root-containers/).

## Supported tags and respective `Dockerfile` links

Learn more about the Bitnami tagging policy and the difference between rolling tags and immutable tags [in our documentation page](https://docs.bitnami.com/tutorials/understand-rolling-tags-containers/).


* [`1`, `1-debian-11`, `1.0.0`, `1.0.0-debian-11-r0`, `latest` (1/debian-11/Dockerfile)](https://github.com/bitnami/containers/blob/main/bitnami/kubernetes-event-exporter/1/debian-11/Dockerfile)
* [`0`, `0-debian-11`, `0.11.0`, `0.11.0-debian-11-r43` (0/debian-11/Dockerfile)](https://github.com/bitnami/containers/blob/main/bitnami/kubernetes-event-exporter/0/debian-11/Dockerfile)

## Connecting to other containers

Using [Docker container networking](https://docs.docker.com/engine/userguide/networking/), a different server running inside a container can easily be accessed by your application containers and vice-versa.

Containers attached to the same network can communicate with each other using the container name as the hostname.

## Configuration

Kubernetes Event Exporter is a tool created to be run inside a pod running on Kubernetes and as such, it will not work if used as a standalone container.

Configuration is done via a YAML file, when run in Kubernetes, it's in ConfigMap. The tool watches all the events and user has to option to filter out some events, according to their properties.

For further documentation, please check [Kubernetes Event Exporter documentation](https://github.com/resmoio/kubernetes-event-exporter#configuration).

## Logging

The Bitnami Kubernetes Event Exporter Docker image sends the container logs to the `stdout`. To view the logs:

```console
$ docker logs kubernetes-event-exporter
```

You can configure the containers [logging driver](https://docs.docker.com/engine/admin/logging/overview/) using the `--log-driver` option if you wish to consume the container logs differently. In the default configuration docker uses the `json-file` driver.

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
