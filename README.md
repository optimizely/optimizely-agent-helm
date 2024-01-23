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
helm install --values myvalues.yaml my-agent optimizely-agent/agent --version [CURRENT_VERSION]
```

or 

```shell
helm install --set nameOverride=abc123 my-agent optimizely-agent/agent --version [CURRENT_VERSION]
```

For more information, view the [Helm install documentation](https://helm.sh/docs/helm/helm_install/) or install through [Artifact Hub](https://artifacthub.io/packages/helm/optimizely-agent/agent).


## Uninstalling the Chart

To uninstall/delete the `my-agent` deployment:

```console
helm delete my-agent
```

# Configurations
To see all configurable options with detailed comments, visit the [values.yaml](https://github.com/optimizely/optimizely-agent-helm/blob/main/values.yaml) file or run:

```shell
helm show values optimizely-agent/agent
``` 

| Property | Description | Defalut value |
| ---	|--- | --- |
| nameOverride | Replaces the name of the chart in the Chart.yaml file | "" |
| fullnameOverride | Completely replaces the generated name | "" | 
| image.repository | Docker image to be used | optimizely/agent |
| image.tag | Docker image tag | "" | 
| image.pullPolicy | Sets the policy for a container and tag when pulling the image | IfNotPresent |
| imagePullSecrets | If you are using a private registry | [] |
| serviceAccount.create | Specifies whether a service account should be created | true |
| serviceAccount.name| Optional - the name of the service account to use | "" |
| serviceAccount.annotations | Optional - annotations to add to the service account | {} |
| replicaCount | Number of deployment replicas | 1 |
| autoscaling.enabled | To allow and configure autoscaling | false |
| autoscaling.minReplicas | Minimum number of replicas | 1 |
| autoscaling.maxReplicas | Maximum number of replicas | 100 |
| autoscaling.targetCPUUtilizationPercentage | Set target percent of CPU utilization | 80 |
| autoscaling.targetMemoryUtilizationPercentage | Set target percent of memory utilization | 80 |
| nodeSelector | To constrain Pods to nodes with specific labels | {} |
| affinity | Sets the affinity Kubernetes attribute for Pods | {} |
| tolerations | Tolerations to apply to Pods | [] |
| podAnnotations | A map with Kubernetes annotations | {} |
| podSecurityContext | The security settings that you specify for a Pod apply to all Containers in the Pod | {} | 
| securityContext | The security settings that you specify for agent container | {} |
| service.type | The type of network service to use and mapping of incoming ports to targetPorts | ClusterIP |
| service.ports | Ports exposed for Optimizely's Agent functionality | port: 8080, port: 8085, port: 8088 |
| ingress.enabled  |  Exposes HTTP and HTTPS routes from outside the cluster to services within the cluster | false | 
| resources | Set a custom container | {} |
| logs.level | Configure logging level for Optimizely specific  logs | debug |
| logs.pretty | Enable pretty print for Optimizely specific logs | true |
| log.includeSdkKey | Enable SDK key in logs for Optimizely specific logs | true |
| env.variables | Environment values for variables | {} |
| env.secrets | Environment values for secrets | {} |
| config | Optimizely client instance configuration properties | See [values.yaml](https://github.com/optimizely/optimizely-agent-helm/blob/main/values.yaml) for defaults |

## Links

* <https://github.com/optimizely/agent>
* <https://docs.developers.optimizely.com/experimentation/v4.0.0-full-stack/docs/optimizely-agent>
* [Optimizely Agent Helm Chart](https://artifacthub.io/packages/helm/optimizely-agent/agent)
* [Configuration file reference](https://github.com/optimizely/agent/blob/master/config.yaml)
