# health-infra

Infraestrutura GitOps da Health Data Platform, gerida via Argo CD.

## Estrutura

- `namespaces/datacluster.yaml` — namespace principal da plataforma
- `argocd/project.yaml` — AppProject do Argo CD
- `argocd/applications/*.yaml` — Applications para cada componente

## Fluxo

1. Instalar Argo CD no cluster (namespace `argocd`).
2. Aplicar:
    - `namespaces/datacluster.yaml`
    - `argocd/project.yaml`
    - todos os ficheiros em `argocd/applications/`
3. Argo CD sincroniza:
    - `health-hapi-fhir`
    - `hl7-v2-connector`
    - `health-fhir-processor`
    - `health-redpanda`
    - `health-postgres`
