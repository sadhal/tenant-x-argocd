# tenant-x-argocd

Manage ArgoCD projects and applications.  

### install argocd reconciler

Follow instructions in https://github.com/sadhal/ns-reconciler with newly created cluster's name.  
`ns-reconciler` will use cluster's kustomization.yaml found in [overlays](overlays/). Overlay kustomization will point out [bases](bases/). Bases have own kustomization.yaml which includes resources that will be created eg. namespaces, argocd projects, argocd applications etc.  

#### setup ArgoCD projects

`ns-reconciler` does that automatically. Changes done to ArgoCD projects need to be commited to GitHub. Pull Request to this repository could be used for that purpose.  

#### setup ArgoCD applications

`ns-reconciler` does that automatically. Changes done to ArgoCD applications need to be commited to GitHub. Pull Request to this repository could be used for that purpose.  
