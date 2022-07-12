# Optimizely Agent Helm Chart

This repository contains a Helm chart to make it easy to host Optimizely Agent in your own Kubernetes infrastructure. The Optimizely Agent allows you to run a proxy to Optimizely in your own infrastructure, to help prevent adblockers from interfering with A/B tests. 

## Installation

To install the chart with the release name `my-agent`:

```shell
helm repo add optimizely-agent https://optimizely.github.io/optimizely-agent-helm
helm install my-agent optimizely-agent/agent
```

## Modifying values

- To override values in a chart:
   - use the `--values` flag and pass in a file.
   - use the `--set` flag and pass configuration from the command line.
- Use the `--set-file` flag to set individual values from a file when the value itself is too long for the command line or is dynamically generated.
- To force a string value use `--set-string`. 

For example:

```shell
helm install --values myvalues.yaml my-agent optimizely-agent/agent
```

or 

```shell
helm install --set nameOverride=abc123 my-agent optimizely-agent/agent
```

For more information, view the [Helm install documentation](https://helm.sh/docs/helm/helm_install/).


## Uninstalling the Chart

To uninstall/delete the `my-agent` deployment:

```console
helm delete my-agent
```

# Configurations

|   Property	|  Description 	|
|---	|---	|
|replicaCount| Number of deployment replicas	|
|image 	|Docker image to be used	|
| autoscaling  	| To allow and configure autoscaling  	|
| nameOverride  	|  Replaces the name of the chart in the Chart.yaml file 	|
|fullnameOverride   	| Completely replaces the generated name  	|
| serviceAccount  	| Specifies whether a service account should be created  	|
| podAnnotations  	| A map with Kubernetes annotations  	|
| podSecurityContext  	|  The security settings that you specify for a Pod apply to all Containers in the Pod 	|
|   securityContext	|   The security settings that you specify for agent container	|
|   env	| Environment variables and secrets  	|
| service  	|  The type of network service to use and mapping of incoming ports to targetPorts |
| ingress  	|  Exposes HTTP and HTTPS routes from outside the cluster to services within the cluster 	|
|  nodeSelector 	|  To constrain Pods to nodes with specific labels 	|
|  tolerations 	| Tolerations to apply to Pods  	|
|  affinity 	| Sets the affinity Kubernetes attribute for Pods  	|
|  config 	| Optimizely client instance configuration properties  	|

## Links

* <https://github.com/optimizely/agent>
* <https://docs.developers.optimizely.com/experimentation/v4.0.0-full-stack/docs/optimizely-agent>
* [Optimizely Agent Helm Chart](https://artifacthub.io/packages/helm/optimizely-agent/agent)
* [Configuration file reference](https://github.com/optimizely/agent/blob/master/config.yaml)
