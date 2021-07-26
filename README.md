# metallb-package

This package provides metallb functionality using [metallb](https://metallb.universe.tf/).

## Components

* metallb

## Configuration

The following configuration values can be set to customize the metallb installation.

### Global

| Value | Required/Optional | Description |
|-------|-------------------|-------------|
| `namespace` | Optional | The namespace in which to deploy metallb. |
| `ip_range`  | Required | IP range to use for the LoadBalancers. (e.g.: 192.168.65.100-192.168.65.100) |

## Usage Example

This walkthrough guides you through using metallb...

## Develop checklist

1. Update your [config.json](./config.json) with the package info
2. Update your [vendir.yml](./src/bundle/vendir.yml) with your upstreams
3. `vendir sync` in `src/bundle` to fetch your new upstream files
4. Add [overlays](./src/bundle/config/overlays/) and [values](./src/bundle/config/values.yaml)
5. Update your [bundle.yml](./src/bundle/.imgpkg/bundle.yml) file
6. Test your bundle: `ytt -f config -v ip_range="192.168.65.100-192.168.65.100"`
7. Lock images used: `kbld -f . --imgpkg-lock-output .imgpkg/images.yml`
8. Publish your bundle: `imgpkg push --bundle quay.io/failk8s/<NAME>-package:<VERSION> --file .`. These steps can be done via [hack/build-package.sh](./hack/build-package.sh)
9. Package up your k8s manifests and test in k8s [hack/package-manifests.sh](./hack/package-manifests.sh). The files will be in `target` folder.