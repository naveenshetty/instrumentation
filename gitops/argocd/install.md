Install Argo CD using manifests

`kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`

to access argocd , we need to expose service 
`kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
`
hit the alb dns on browser , username admin , for password run below command
`kubectl get secrets -n argocd 
`
`kubectl edit secret argocd-initial-admin-secret -n argocd
`
get password, it is base64 encoded one so decode it
`echo d3pVeFhKcDRsUExSNHZubw== | base64 --decode
`
access argocd from browser using external IP in 
`kubectl get svc -n argocd
`