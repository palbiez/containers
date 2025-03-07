# Jupyter Base Notebook packaged by Bitnami

## What is Jupyter Base Notebook?

> Jupyter Base Notebook is an instance of Jupyter Notebook for your JupyterHub installation. The Base flavor contains the essential Python 3 packages and the JupyterLab user interface.

[Overview of Jupyter Base Notebook](https://github.com/jupyter/docker-stacks)

Trademarks: This software listing is packaged by Bitnami. The respective trademarks mentioned in the offering are owned by the respective companies, and use of them does not imply any affiliation or endorsement.

## TL;DR

```console
$ docker run --name jupyter-base-notebook bitnami/jupyter-base-notebook:latest
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


* [`3`, `3-debian-11`, `3.0.0`, `3.0.0-debian-11-r3`, `latest` (3/debian-11/Dockerfile)](https://github.com/bitnami/containers/blob/main/bitnami/jupyter-base-notebook/3/debian-11/Dockerfile)
* [`2`, `2-debian-11`, `2.3.1`, `2.3.1-debian-11-r45` (2/debian-11/Dockerfile)](https://github.com/bitnami/containers/blob/main/bitnami/jupyter-base-notebook/2/debian-11/Dockerfile)
* [`1`, `1-debian-11`, `1.5.0`, `1.5.0-debian-11-r45` (1/debian-11/Dockerfile)](https://github.com/bitnami/containers/blob/main/bitnami/jupyter-base-notebook/1/debian-11/Dockerfile)

Subscribe to project updates by watching the [bitnami/containers GitHub repo](https://github.com/bitnami/containers).

## Get this image

The recommended way to get the Bitnami jupyter-base-notebook Docker Image is to pull the prebuilt image from the [Docker Hub Registry](https://hub.docker.com/r/bitnami/jupyter-base-notebook).

```console
$ docker pull bitnami/jupyter-base-notebook:latest
```

To use a specific version, you can pull a versioned tag. You can view the [list of available versions](https://hub.docker.com/r/bitnami/jupyter-base-notebook/tags/) in the Docker Hub Registry.

```console
$ docker pull bitnami/jupyter-base-notebook:[TAG]
```

If you wish, you can also build the image yourself by cloning the repository, changing to the directory containing the Dockerfile and executing the `docker build` command. Remember to replace the `APP`, `VERSION` and `OPERATING-SYSTEM` path placeholders in the example command below with the correct values.

```console
$ git clone https://github.com/bitnami/containers.git
$ cd bitnami/APP/VERSION/OPERATING-SYSTEM
$ docker build -t bitnami/APP:latest .
```

## Why use a non-root container?

Non-root container images add an extra layer of security and are generally recommended for production environments. However, because they run as a non-root user, privileged tasks are typically off-limits. Learn more about non-root containers [in our docs](https://docs.bitnami.com/tutorials/work-with-non-root-containers/).

## Configuration

### Running commands

To run commands inside this container you can use `docker run`, for example to execute `jupyterhub-singleuser --version` you can follow the example below:

```console
$ docker run --rm --name jupyter-base-notebook bitnami/jupyter-base-notebook:latest -- jupyterhub-singleuser --version
```

Check the [official Jupyter Notebook documentation](https://jupyter.readthedocs.io/en/latest/running.html) for a list of the available parameters.

### Adding more python packages

To add more python packages, you need to create a Dockerfile extending the current image, and the commands to install the desired packages.
In the following example, the base notebook image is used to add `scipy` and `matplotlib`.

```Dockerfile
FROM bitnami/jupyter-base-notebook:latest
USER root
RUN conda install --quiet --yes \
    'matplotlib-base' \
    'scipy' && \
    conda clean --all -f -y
USER 1001
```

## Branch Deprecation Notice

Jupyter Base Notebook's branch 1 and 2 are no longer maintained by upstream and are now internally tagged as to be deprecated. These branches will no longer be released in our catalog a month after this notice is published, but already released container images will still persist in the registries. Valid to be removed starting on: 10-28-2022

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
