azure-devops-agents
===================
Helm chart for Azure Devops agent pool

Current chart version is `1.0.0`





## Chart Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| azpAgentName | string | `"$HOSTNAME"` |  |
| azpPool | string | `"kubernetes-azdo-agents"` |  |
| azpToken | string | `nil` |  |
| azpUrl | string | `nil` |  |
| extraEnv | object | `{}` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"quay.io/xenitab/azp-agent"` |  |
| image.tag | string | `"ubuntu-16.04"` |  |
| nodeSelector | object | `{}` |  |
| replicas | int | `2` |  |
| resources.limits.cpu | int | `2` |  |
| resources.limits.memory | string | `"4Gi"` |  |
| resources.requests.cpu | int | `1` |  |
| resources.requests.memory | string | `"1Gi"` |  |
| tolerations | list | `[]` |  |
