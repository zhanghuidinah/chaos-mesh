# Set up the development environment

This document walks you through the environment setup process for Chaos Mesh development.

## Prerequisites

- [golang](https://golang.org/dl/) (>= v1.13)
- [docker](https://www.docker.com/)
- [gcc](https://gcc.gnu.org/)
- [Helm](https://helm.sh/) >= v2.8.2
- [kind](https://github.com/kubernetes-sigs/kind)
- [yarn](https://yarnpkg.com/lang/en/) and [nodejs](https://nodejs.org/en/) (for chaos-dashboard)

## Prepare the toolchain

Make sure you have the above prerequisites met. Now follow the steps below to prepare the toolchain for compiling Chaos Mesh:

1. Clone the chaos-mesh repo to your local machine.

```
git clone https://github.com/pingcap/chaos-mesh.git
cd chaos-mesh
```

2. Install the K8s API development framework - [kubebuilder](https://github.com/kubernetes-sigs/kubebuilder) and [kustomize](https://github.com/kubernetes-sigs/kustomize).

```
make install-kubebuilder
make install-kustomize
```

3. Start the docker service. Most Linux distributions use `systemctl` to start services. If you do not have `systemctl`, use the service command.

4. Make sure `${GOPATH}/bin` is in your `PATH` by executing:
 `echo 'export PATH=$(go env GOPATH)/bin:${PATH}' >> ~/.bash_profile` and `source ~/. bash_profile`.

> **Note:**
>
> If your yarn is newly installed, you may need to restart the terminal to make it available.

Now you can test the toolchain by running:

```
make
```

If there is no error in the output, the compiling toolchain is successfully configured.

## Prepare the deployment environment

With the toolchain ready, you still need a local Kubernetes cluster as the deployment environment. Because kind is already installed, you can now set up the K8s cluster directly:

```
hack/kind-cluster-build.sh
```

## Next steps

Congratulations! You are now all set up for Chaos Mesh development. Try the following tasks:

- [Develop a New Chaos Type](./dev_hello_world.md)
- [ ] [Add facilities to chaos daemon]
