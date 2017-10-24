# Google Cloud Container Builder community images

This repository contains source code for community-contributed builders used with the [Google Cloud Container
Builder API](https://cloud.google.com/container-builder/docs/).

These are not official Google products.

## How to use

First, enable your project, enable the Container Builder API, and initialize the
Cloud SDK following the instructions in the [Docker
Quickstart](https://cloud.google.com/container-builder/docs/quickstart-docker).

Then, download the source code and build your builder.  For example, to setup
the `packer` builder using a Linux or Mac OS X workstation:

```sh
$ git clone http://github.com/GoogleCloudPlatform/cloud-builders-community
$ cd cloud-builders-community/packer
$ gcloud container builds submit --config cloudbuild.yaml .
```

View the builder image in Google Container Registry:

```sh
$ gcloud container images list --filter packer
```

Then, use the builder in your own project's `cloudbuild.yaml`:

```yaml
- name: 'gcr.io/$PROJECT_ID/packer'
  args:
  - build
  - -var
  - project_id=$PROJECT_ID
  - packer.json
```

Examples of use are included in each tool's `examples` directory.

## Contributing

We welcome your contributions enthusiastically.  See [CONTRIBUTING](CONTRIBUTING.md) for more information on how to get started.  Please include a `cloudbuild.yaml` and at least one working example in your [pull request](https://help.github.com/articles/about-pull-requests/).

## License

This library is licensed under Apache 2.0. Full license text is available in [LICENSE](LICENSE).

File issues here or e-mail `gcr-contact@google.com` if you have questions about
the usage of these build steps or the Cloud Container Builder API in general.

