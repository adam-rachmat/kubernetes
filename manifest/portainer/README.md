# Deploy PORTAINER Kubernetes

## Deploy With HELM

```
helm upgrade --install --create-namespace -n portainer portainer portainer/portainer --debug \
    --set service.type=ClusterIP \
    --set tls.force=true \
    --set ingress.enabled=true \
    --set ingress.ingressClassName=public \
    --set ingress.hosts[0].host=portainer.kube.modalsemangat.com \
    --set ingress.hosts[0].paths[0].path="/" \
    --set ingress.certManager=true \
    --set ingress.tls[0].hosts[0]=portainer.kube.modalsemangat.com \
    --set ingress.tls[0].secretName=portainer-tls \
    --set ingress.annotations."kubernetes\.io/ingress\.class"=nginx \
    --set ingress.annotations."cert-manager\.io/cluster-issuer"=lets-encrypt \
    --set ingress.annotations."nginx\.ingress\.kubernetes\.io/backend-protocol"=HTTPS \
    --set persistence.storageClass=nfs-csi \
    --set persistence.size=1Gi
```