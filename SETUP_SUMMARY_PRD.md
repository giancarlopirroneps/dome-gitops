
    k config use-context cluster-admin@DOME-Production-K8S
    create ns argocd
    kubectl apply -f applications_prd/namespaces.yaml -n argocd
    kubectl apply -k ./extension/ -n argocd
    kubectl apply -f applications/namespaces.yaml -n argocd
    kubectl apply -f applications/sealed-secrets.yaml -n argocd
    kubectl apply -f applications/ingress.yaml -n argocd

    # test ingress
    k create ns echoserver
    k apply -f ionos_prd/external-dns-ionos-webhook/test-ingress/echoserver_app_no_domain.yaml
    curl http://212.132.90.194/test
    



