## Create a project with role
Define and create argo cd project declaratively with below specs:
- Allow all sources (repos)
- allow all destinations
- allow all cluster and namespaces scoped resources
- Define a role with has a sync permission to all applications in the same project
- Create a token related to this role
- try delete an application using this token, argoCD should deny this action
