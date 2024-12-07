Step -1: Install K8S[Minikube or Master WorkerNodes] and ArgoCD[https://argo-cd.readthedocs.io/en/stable/getting_started/]
Note: kubectl create namespace ---- Before going to step 2, we have to create namespace for argocd.
Step -2: kubectl get pods -n argocd -w

Step -3: kubectl get svc -n argocd

Step -4: kubectl edit svc argocd-server -n argocd

Step -5: minikube service list -n argocd

Step -6: minikube service argocd-server -n argocd  # ArgoCD runs on port 80 & 443.

Step -7: kubectl port-forward --address 0.0.0.0 svc/argocd-server -n argocd 8080:443   

# To access the argocd copy public ip of ec2 and 8080 port to access the argocd UI.
# It's making the service available on your computer through port 8080, even though the service itself runs on port 443 in the Kubernetes system.
# --address 0.0.0.0 part just means it's open for connections from anywhere.

Step -8: kubectl edit secret argocd-initial-admin-secret -n argocd    # To login into argocd we have know password.
                                                                      # We have to encrypt and decrypt.
Step -9: echo copypasswd by moving into above cmd | base64 --decode
