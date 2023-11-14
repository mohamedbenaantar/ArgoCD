## Creare an application with manifests synced as below:
- One Job in PreSync Phase, this job should be deleted once Succeeded
- One Job in Sync Phase, this job should be deleted if new resource is created
- One Job in PostSync Phase, this job should be deleted if failed
- Add a job manifest that will be skipped by ArgoCD
