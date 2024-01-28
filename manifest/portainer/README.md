# Deploy PORTAINER Kubernetes

## Install With HELM

```
helm upgrade --install --create-namespace -n portainer portainer portainer/portainer --debug \
    --set service.type=ClusterIP \
    --set tls.force=true \
    --set ingress.enabled=true \
    --set ingress.ingressClassName=public \
    --set ingress.annotations."nginx\.ingress\.kubernetes\.io/backend-protocol"=HTTPS \
    --set ingress.annotations."cert-manager\.io/cluster-issuer"=lets-encrypt \
    --set ingress.hosts[0].host=portainer.kube.modalsemangat.com \
    --set ingress.hosts[0].paths[0].path="/" \
    --set persistence.storageClass=nfs-csi
```
