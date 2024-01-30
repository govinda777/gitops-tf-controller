# gitops-tf-controller
gitops-tf-controller https://docs.gitops.weave.works/docs/terraform/get-started-terraform/

0 - Limpe seu ambiente 

docker system prune
docker volume prune

1 - crie um novo cluster

minikube start --profile tf-controller


kind create cluster --name tf-controller

➜ ~ kind create cluster --name tf-controller
Creating cluster "tf-controller" ...
 ✓ Ensuring node image (kindest/node:v1.27.3) 🖼
 ✓ Preparing nodes 📦
 ✓ Writing configuration 📜
 ✓ Starting control-plane 🕹️
 ✓ Installing CNI 🔌
 ✓ Installing StorageClass 💾
Set kubectl context to "kind-tf-controller"
You can now use your cluster with:

kubectl cluster-info --context kind-tf-controller



Have a question, bug, or feature request? Let us know! https://kind.sigs.k8s.io/#community 🙂
➜ ~

0 - Delete o cluster

kind delete cluster --name tf-controller

1 - Crie um novo namepace

kind create cluster --name tf-controller

minikube start --profile tf-controller

Verificar o Status do Cluster:

minikube status --profile tf-controller


--

2 

export GITHUB_USER=govinda777

flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=gitops-tf-controller \
  --branch=main \
   --path=./cluster/my-cluster \
   --personal \
   --token-auth

---

kubectl create secret generic aws-credentials \
--namespace=flux-system \
--from-literal=AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID \
--from-literal=AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY

