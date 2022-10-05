#### INICIALIZAR O ARGO CD <br>
Checar se o MINIKUBE está rodando na máquina
> $ check com "minikube status" <br>

> $ kubectl create namespace argocd

> $ kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

> $ kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

> $ kubectl port-forward svc/argocd-server -n argocd 8080:443

** Acessar o link da aplicação (https://localhost:8080)


#### Gerar a senha de primeiro acesso:

> $ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

* Copiar a senha e logar como "admin" e a senha gerada.
Após ir no "User info" e "Update Password"

Após atualizar a senha ir na aba "Manage Your repositores" e cadastrar o repositório: "https://github.com/DiegoGrimon/ArgoCD.git"

Ir na opção "+ NEW APP" e cadastrar a aplicação que está na pasta k8s

#### Aplicação Exemplo ARGOCD

Ir na aba "Manage Your repositores" e cadastrar o repositório: https://github.com/argoproj/argocd-example-apps.git

Em seguida ir na aba principal e criar um projeto chamado: "gestbook"
selecione: <br>
Project -> Default <br>
Cluster: https://kubernetes.default.svc <br>
Repo URL: https://github.com/argoproj/argocd-example-apps.git <br>
Path (selecione): apps <br>

Em seguida clique no botão "CREATE"
