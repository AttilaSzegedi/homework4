# homework4

# create name spaces
kubectl create namespace hw4-dev
namespace/hw4-dev created
PS C:\CUBIX\devops\kubernetes\homework4\kustomize> kubectl create namespace hw4-prod
namespace/hw4-prod created
PS C:\CUBIX\devops\kubernetes\homework4\kustomize> kubectl create namespace hw4-test
namespace/hw4-test created

# check the kustomization:
kubectl kustomize overlay/dev
kubectl kustomize overlay/test
kubectl kustomize overlay/prod

# install/apply 
kubectl apply -k overlay/test
kubectl apply -k overlay/dev
kubectl apply -k overlay/prod

# test the dev system
kubectl logs -l app=frontapp --all-containers=true -n hw4-dev
kubectl logs -l app=backapp --all-containers=true -n hw4-dev

# delete namespace
kubectl delete namespace hw4-test
kubectl delete namespace hw4-prod
kubectl delete namespace hw4-dev