# Sealed Secrets packaged by Bitnami

## What is Sealed Secrets?

> Sealed Secrets are "one-way" encrypted K8s Secrets that can be created by anyone, but can only be decrypted by the controller running in the target cluster recovering the original object.

[Overview of Sealed Secrets](https://github.com/bitnami-labs/sealed-secrets)



## TL;DR

```console
$ docker run --name sealed-secrets bitnami/sealed-secrets:latest
```

## Why use Bitnami Images?

* Bitnami closely tracks upstream source changes and promptly publishes new versions of this image using our automated systems.
* With Bitnami images the latest bug fixes and features are available as soon as possible.
* Bitnami containers, virtual machines and cloud images use the same components and configuration approach - making it easy to switch between formats based on your project needs.
* All our images are based on [minideb](https://github.com/bitnami/minideb) a minimalist Debian based container image which gives you a small base container image and the familiarity of a leading Linux distribution.
* All Bitnami images available in Docker Hub are signed with [Docker Content Trust (DCT)](https://docs.docker.com/engine/security/trust/content_trust/). You can use `DOCKER_CONTENT_TRUST=1` to verify the integrity of the images.
* Bitnami container images are released on a regular basis with the latest distribution packages available.

## Supported tags and respective `Dockerfile` links

Learn more about the Bitnami tagging policy and the difference between rolling tags and immutable tags [in our documentation page](https://docs.bitnami.com/tutorials/understand-rolling-tags-containers/).


* [`0`, `0-scratch`, `0.18.5`, `0.18.5-scratch-r2`, `latest` (0/scratch/Dockerfile)](https://github.com/bitnami/containers/blob/main/bitnami/sealed-secrets/0/scratch/Dockerfile)

Subscribe to project updates by watching the [bitnami/containers GitHub repo](https://github.com/bitnami/containers).

## Get this image

The recommended way to get the Bitnami sealed-secrets Docker Image is to pull the prebuilt image from the [Docker Hub Registry](https://hub.docker.com/r/bitnami/sealed-secrets).

```console
$ docker pull bitnami/sealed-secrets:latest
```

To use a specific version, you can pull a versioned tag. You can view the [list of available versions](https://hub.docker.com/r/bitnami/sealed-secrets/tags/) in the Docker Hub Registry.

```console
$ docker pull bitnami/sealed-secrets:[TAG]
```

If you wish, you can also build the image yourself by cloning the repository, changing to the directory containing the Dockerfile and executing the `docker build` command. Remember to replace the `APP`, `VERSION` and `OPERATING-SYSTEM` path placeholders in the example command below with the correct values.

```console
$ git clone https://github.com/bitnami/containers.git
$ cd bitnami/APP/VERSION/OPERATING-SYSTEM
$ docker build -t bitnami/APP:latest .
```

## Configuration

### Running commands

To run commands inside this container you can use `docker run`, for example to execute `kubeseal --version` you can follow the example below:

```console
$ docker run --rm --name sealed-secrets bitnami/sealed-secrets:latest -- kubeseal --version
```

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
