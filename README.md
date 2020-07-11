# tenant-x-argocd

Manage ArgoCD projects and applications.  

## install argocd reconciler

Follow instructions in https://github.com/sadhal/ns-reconciler with newly created cluster's name.  
`ns-reconciler` will use cluster's kustomization.yaml found in [overlays](overlays/). Overlay kustomization will point out [bases](bases/). Bases have own kustomization.yaml which includes resources that will be created eg. namespaces, argocd projects, argocd applications etc.  
Fix RBAC for serviceaccount `system:serviceaccount:argocd:argocd-application-controller`  

```bash
$ oc adm policy add-cluster-role-to-user edit system:serviceaccount:argocd:argocd-application-controller
```

### setup ArgoCD projects

`ns-reconciler` does that automatically. Changes done to ArgoCD projects need to be commited to GitHub. Pull Request to this repository could be used for that purpose.  
ArgoCD projects must have unique names. Use subtenant name as project names.  

### setup ArgoCD applications

`ns-reconciler` does that automatically. Changes done to ArgoCD applications need to be commited to GitHub. Pull Request to this repository could be used for that purpose.  
ArgoCD applications must have unique names. Use pattern <subtenant name>-<namespace name>-<application-name> which will allow motion of subtenants and their applications to different clusters.  