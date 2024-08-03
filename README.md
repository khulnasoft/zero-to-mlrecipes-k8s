# Zero to MLRecipes with Kubernetes

This repo contains a *Helm chart* for [MLRecipes](https://github.com/khulnasoft/ml-recipes) and a guide to use it. Together,
they allow you to make a JupyterHub available to a very large group of users such as the staff and students of a university.

## MLRecipes Modifications

In this repo, we made some modifications to the forked repo and its helm chart and default values so that it works with the [ml-recipes](https://github.com/khulnasoft/ml-recipes) and [ml-workspace](https://github.com/khulnasoft/ml-workspace) images. Hence, we do not use the hub or singleuser-sample image in the images/ directory.
For most parts you should be able to follow the comprehensive guide linked below.

Most prominent changes: 
- change of the command fields in hub and proxy yamls
- modifying ports to make tunnelling of ssh possible
- changes of default values, e.g. the used images
- changes of paths, e.g. the ssl secret mount path

We do not push the helm chart to a repository for now, so feel free to download it from the [mlhub releases page](https://github.com/khulnasoft/ml-recipes/releases) or to create the package yourself via `helm package jupyterhub/`.

You can then deploy the chart via `helm upgrade --install mlhub packaged-chart.tgz --namespace $namespace --values config.yaml`.
The config.yaml can be used to overrride default values.

---
<br/>

# Original Readme:

## The guide

The [Zero to JupyterHub with Kubernetes guide](https://z2jh.jupyter.org)
provides user-friendly steps to _deploy_
[JupyterHub](https://github.com/jupyterhub/jupyterhub) on a cloud using
[Kubernetes](https://kubernetes.io/) and [Helm](https://helm.sh/).

The guide is complemented well by the [documentation for JupyterHub](https://jupyterhub.readthedocs.io).

## The Helm chart

The JupyterHub Helm chart lets a user create a reproducible and maintainable
deployment of JupyterHub on a Kubernetes cluster in a cloud environment. The
released charts are made available in our [Helm chart
repository](https://jupyterhub.github.io/helm-chart).

## History

Much of the initial groundwork for this documentation is information learned
from the successful use of JupyterHub and Kubernetes at UC Berkeley in their
[Data 8](http://data8.org/) program.

![](doc/source/_static/images/data8_audience.jpg)

## Acknowledgements

Thank you to the following contributors:

- Aaron Culich
- Carol Willing
- Chris Holdgraf
- Erik Sundell
- Ryan Lovett
- Yuvi Panda

Future contributors are encouraged to add themselves to this README file too.

## Licensing

This repository is dual licensed under the Apache2 (to match the upstream
Kubernetes [charts](https://github.com/helm/charts) repository) and
3-clause BSD (to match the rest of Project Jupyter repositories) licenses. See
the `LICENSE` file for more information!
