# gitops-tf-controller
gitops-tf-controller https://docs.gitops.weave.works/docs/terraform/get-started-terraform/


flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=gitops-tf-controller \
  --branch=main \
   --path=./cluster/tf-controller \
   --personal \
   --token-auth
