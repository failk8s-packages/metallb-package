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
2. Add [overlays](./src/bundle/config/overlays/) and [values](./src/bundle/config/values.yaml)
3. Test your bundle: `ytt --data-values-file src/example-values/minikube.yaml  -f target/bundle/config` providing a sample values file from [example-values](./src/examples-values/)
4. Build your bundle `./hack/build.sh`
5. Add it to the [failk8s-repo](https://github.com/failk8s-packages/failk8s-repo) and publish the new repo and test the package from there, or [test with local files](./target/test)

**NOTE**: `develop` versions will not be image locked and will have a version of 0.0.0+develop to comply with semver.