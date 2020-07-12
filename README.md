# tenant-x-argocd

Manage ArgoCD projects and applications.  
ArgoCD will be used as GitOps tool from both test and production clusters.  
Applications within test clusters are listening for changes to `staging` branch in config repos. 
Applications within prod clusters are listening for changes to `master` branch in config repos. 


### setup ArgoCD projects

`tenant-x` repo does that automatically with ArgoCD Application which reconciles Appproject manifests to a given cluster and namespace. Changes done to ArgoCD projects need to be commited to GitHub. Pull Request to this repository could be used for that purpose.  
ArgoCD projects must have unique names. Use subtenant name as project names.  
Do not remove projects before removing all its applications. Application deletion will fail if it's parent (appproject) is missing. Workaround for that is to update applications yaml and set `default` as Appproject.  

### setup ArgoCD applications

`tenant-x` repo does that automatically with ArgoCD Application which reconciles Application manifests to a given cluster and namespace. Changes done to ArgoCD applications need to be commited to GitHub. Pull Request to this repository could be used for that purpose.  
ArgoCD applications must have unique names. Use pattern <subtenant name>-<namespace name>-<application-name> which will allow motion of subtenants and their applications to different clusters.  