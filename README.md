```
|--⫸  az group create -l westus -n runItOnCloud                                                                                                                                                          🔂
|~ 💻
|
|--⫸  az aks create \                                                                                                                                                                                    🔂
    --resource-group runitoncloud-tf \
    --name runitonCloud \
    --node-count 2 \
    --generate-ssh-keys \
    --attach-acr runitoncloud
{- Finished ..
  "aadProfile": null,
  "addonProfiles": {
    "KubeDashboard": {
      "config": null,
      "enabled": true,
      "identity": null
    }
  },
  "agentPoolProfiles": [
    {
      "availabilityZones": null,
      "count": 2,
      "enableAutoScaling": null,
      "enableNodePublicIp": false,
      "maxCount": null,
      "maxPods": 110,
      "minCount": null,
      "mode": "System",
      "name": "nodepool1",
      "nodeLabels": {},
      "nodeTaints": null,
      "orchestratorVersion": "1.16.10",
      "osDiskSizeGb": 128,
      "osType": "Linux",
      "provisioningState": "Succeeded",
      "scaleSetEvictionPolicy": null,
      "scaleSetPriority": null,
      "spotMaxPrice": null,
      "tags": null,
      "type": "VirtualMachineScaleSets",
      "vmSize": "Standard_DS2_v2",
      "vnetSubnetId": null
    }
  ],
  "apiServerAccessProfile": null,
  "autoScalerProfile": null,
  "diskEncryptionSetId": null,
  "dnsPrefix": "runitonClo-runitoncloud-tf-d03598",
  "enablePodSecurityPolicy": null,
  "enableRbac": true,
  "fqdn": "runitonclo-runitoncloud-tf-d03598-727b6814.hcp.westeurope.azmk8s.io",
  "id": "/subscriptions/d0359825-dc9e-4f37-b195-2e5148b4923e/resourcegroups/runitoncloud-tf/providers/Microsoft.ContainerService/managedClusters/runitonCloud",
  "identity": null,
  "identityProfile": null,
  "kubernetesVersion": "1.16.10",
  "linuxProfile": {
    "adminUsername": "azureuser",
    "ssh": {
      "publicKeys": [
        {
          "keyData": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCwcpcdKVemN639FwzKdEz/BjlkmsEDeQTOB5zZ0cpH+ZQwMB5N4Fkk+StqjskeSV9Tn6ZW3MiMPB94aXOIrIuC2GU5B9L5bEplB9PjUxzr9pxTaDCnPXHaRIbElDEUV0BsJywf3cAyO6rhA1kcLfOj3ZoSSmq4XcvRVqITDWJNUfteWTKySMKRdMfeQQj1UO4SSGg9p+HqcaWn7K87Oz8wWAS7M5Z+2+zV9U4AhE0qqkTJtADqd1IzXPnvedxfnMOa9m7leg2812I73l70iuQzB8Gmab+WjGS6SLI2zC61cGViXMWvHqEujns9W4atyWXTeXiwx+mbPVkF3sJBSJyf aymensegni@Aymens-MBP.fritz.box\n"
        }
      ]
    }
  },
  "location": "westeurope",
  "maxAgentPools": 10,
  "name": "runitonCloud",
  "networkProfile": {
    "dnsServiceIp": "10.0.0.10",
    "dockerBridgeCidr": "172.17.0.1/16",
    "loadBalancerProfile": {
      "allocatedOutboundPorts": null,
      "effectiveOutboundIps": [
        {
          "id": "/subscriptions/d0359825-dc9e-4f37-b195-2e5148b4923e/resourceGroups/MC_runitoncloud-tf_runitonCloud_westeurope/providers/Microsoft.Network/publicIPAddresses/c7839e72-4db8-46f4-9707-addc84618111",
          "resourceGroup": "MC_runitoncloud-tf_runitonCloud_westeurope"
        }
      ],
      "idleTimeoutInMinutes": null,
      "managedOutboundIps": {
        "count": 1
      },
      "outboundIpPrefixes": null,
      "outboundIps": null
    },
    "loadBalancerSku": "Standard",
    "networkMode": null,
    "networkPlugin": "kubenet",
    "networkPolicy": null,
    "outboundType": "loadBalancer",
    "podCidr": "10.244.0.0/16",
    "serviceCidr": "10.0.0.0/16"
  },
  "nodeResourceGroup": "MC_runitoncloud-tf_runitonCloud_westeurope",
  "privateFqdn": null,
  "provisioningState": "Succeeded",
  "resourceGroup": "runitoncloud-tf",
  "servicePrincipalProfile": {
    "clientId": "8f71ebe6-4635-4d38-b766-a771e40b3504",
    "secret": null
  },
  "sku": {
    "name": "Basic",
    "tier": "Free"
  },
  "tags": null,
  "type": "Microsoft.ContainerService/ManagedClusters",
  "windowsProfile": null
}
|~ 💻
|
|--⫸  az aks get-credentials --resource-group runitoncloud-tf --name runitonCloud                                                                                                                        🔂
Merged "runitonCloud" as current context in /Users/aymensegni/.kube/config
|~ 💻
|
|--⫸  k get nodes                                                                                                                                                                                        🔂
NAME                                STATUS   ROLES   AGE   VERSION
aks-nodepool1-57319200-vmss000000   Ready    agent   96s   v1.16.10
aks-nodepool1-57319200-vmss000001   Ready    agent   87s   v1.16.10
|~ 💻
|
|--⫸  kubectl apply --filename https://github.com/knative/serving/releases/download/v0.16.0/serving-crds.yaml                                                                                            🔂

customresourcedefinition.apiextensions.k8s.io/certificates.networking.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/configurations.serving.knative.dev created
customresourcedefinition.apiextensions.k8s.io/ingresses.networking.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/metrics.autoscaling.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/podautoscalers.autoscaling.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/revisions.serving.knative.dev created
customresourcedefinition.apiextensions.k8s.io/routes.serving.knative.dev created
customresourcedefinition.apiextensions.k8s.io/serverlessservices.networking.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/services.serving.knative.dev created
customresourcedefinition.apiextensions.k8s.io/images.caching.internal.knative.dev created
|~ 💻
|
|--⫸  kubectl apply --filename https://github.com/knative/serving/releases/download/v0.16.0/serving-core.yaml                                                                                            🔂

customresourcedefinition.apiextensions.k8s.io/images.caching.internal.knative.dev unchanged
namespace/knative-serving created
serviceaccount/controller created
clusterrole.rbac.authorization.k8s.io/knative-serving-admin created
clusterrolebinding.rbac.authorization.k8s.io/knative-serving-controller-admin created
image.caching.internal.knative.dev/queue-proxy created
configmap/config-autoscaler created
configmap/config-defaults created
configmap/config-deployment created
configmap/config-domain created
configmap/config-features created
configmap/config-gc created
configmap/config-leader-election created
configmap/config-logging created
configmap/config-network created
configmap/config-observability created
configmap/config-tracing created
horizontalpodautoscaler.autoscaling/activator created
deployment.apps/activator created
service/activator-service created
deployment.apps/autoscaler created
service/autoscaler created
deployment.apps/controller created
service/controller created
deployment.apps/webhook created
service/webhook created
customresourcedefinition.apiextensions.k8s.io/certificates.networking.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/configurations.serving.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/ingresses.networking.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/metrics.autoscaling.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/podautoscalers.autoscaling.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/revisions.serving.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/routes.serving.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/serverlessservices.networking.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/services.serving.knative.dev unchanged
clusterrole.rbac.authorization.k8s.io/knative-serving-addressable-resolver created
clusterrole.rbac.authorization.k8s.io/knative-serving-namespaced-admin created
clusterrole.rbac.authorization.k8s.io/knative-serving-namespaced-edit created
clusterrole.rbac.authorization.k8s.io/knative-serving-namespaced-view created
clusterrole.rbac.authorization.k8s.io/knative-serving-core created
clusterrole.rbac.authorization.k8s.io/knative-serving-podspecable-binding created
validatingwebhookconfiguration.admissionregistration.k8s.io/config.webhook.serving.knative.dev created
mutatingwebhookconfiguration.admissionregistration.k8s.io/webhook.serving.knative.dev created
validatingwebhookconfiguration.admissionregistration.k8s.io/validation.webhook.serving.knative.dev created
secret/webhook-certs created
|~ 💻
|
|--⫸  cat << EOF > ./istio-minimal-operator.yaml                                                                                                                                                         🔂
apiVersion: install.istio.io/v1alpha1
kind: IstioOperator
spec:
  values:
    global:
      proxy:
        autoInject: disabled
      useMCP: false
      # The third-party-jwt is not enabled on all k8s.
      # See: https://istio.io/docs/ops/best-practices/security/\#configure-third-party-service-account-tokens
      jwtPolicy: first-party-jwt

  addonComponents:
    pilot:
      enabled: true
    prometheus:
      enabled: false

  components:
    ingressGateways:
      - name: istio-ingressgateway
        enabled: true
      - name: cluster-local-gateway
        enabled: true
        label:
          istio: cluster-local-gateway
          app: cluster-local-gateway
        k8s:
          service:
            type: ClusterIP
            ports:
            - port: 15020
              name: status-port
            - port: 80
              name: http2
            - port: 443
              name: https
EOF

istioctl manifest apply -f istio-minimal-operator.yaml
zsh: command not found: istioctl
|~ 💻
|
|--⫸  curl -sL https://istio.io/downloadIstioctl | sh -                                                                                                                                                  🔂

Downloading istioctl-1.6.5 from https://github.com/istio/istio/releases/download/1.6.5/istioctl-1.6.5-osx.tar.gz ...
istioctl-1.6.5-osx.tar.gz download complete!

Add the istioctl to your path with:
  export PATH=$PATH:$HOME/.istioctl/bin

Begin the Istio pre-installation verification check by running:
	 istioctl verify-install

Need more information? Visit https://istio.io/docs/reference/commands/istioctl/
|~ 💻
|
|--⫸  export PATH=$PATH:$HOME/.istioctl/bin                                                                                                                                                              🔂

|~ 💻
|
|--⫸  cat << EOF > ./istio-minimal-operator.yaml                                                                                                                                                         🔂
apiVersion: install.istio.io/v1alpha1
kind: IstioOperator
spec:
  values:
    global:
      proxy:
        autoInject: disabled
      useMCP: false
      # The third-party-jwt is not enabled on all k8s.
      # See: https://istio.io/docs/ops/best-practices/security/\#configure-third-party-service-account-tokens
      jwtPolicy: first-party-jwt

  addonComponents:
    pilot:
      enabled: true
    prometheus:
      enabled: false

  components:
    ingressGateways:
      - name: istio-ingressgateway
        enabled: true
      - name: cluster-local-gateway
        enabled: true
        label:
          istio: cluster-local-gateway
          app: cluster-local-gateway
        k8s:
          service:
            type: ClusterIP
            ports:
            - port: 15020
              name: status-port
            - port: 80
              name: http2
            - port: 443
              name: https
EOF

istioctl manifest apply -f istio-minimal-operator.yaml
✔ Istio core installed
✔ Istiod installed
✔ Ingress gateways installed
✔ Addons installed
✔ Installation complete                                                                                                                                                           |~ 💻
|
|--⫸  kubectl label namespace knative-serving istio-injection=enabled                                                                                                          🔂

namespace/knative-serving labeled
|~ 💻
|
|--⫸  cat <<EOF | kubectl apply -f -                                                                                                                                           🔂
apiVersion: "security.istio.io/v1beta1"
kind: "PeerAuthentication"
metadata:
  name: "default"
  namespace: "knative-serving"
spec:
  mtls:
    mode: PERMISSIVE
EOF
peerauthentication.security.istio.io/default created
|~ 💻
|
|--⫸  kubectl apply --filename https://github.com/knative/net-istio/releases/download/v0.16.0/release.yaml                                                                     🔂

clusterrole.rbac.authorization.k8s.io/knative-serving-istio created
gateway.networking.istio.io/knative-ingress-gateway created
gateway.networking.istio.io/cluster-local-gateway created
mutatingwebhookconfiguration.admissionregistration.k8s.io/webhook.istio.networking.internal.knative.dev created
validatingwebhookconfiguration.admissionregistration.k8s.io/config.webhook.istio.networking.internal.knative.dev created
secret/istio-webhook-certs created
configmap/config-istio created
deployment.apps/networking-istio created
deployment.apps/istio-webhook created
service/istio-webhook created
|~ 💻
|
|--⫸  kubectl --namespace istio-system get service istio-ingressgateway                                                                                                        🔂

NAME                   TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)                                                      AGE
istio-ingressgateway   LoadBalancer   10.0.76.127   51.105.98.187   15021:30344/TCP,80:30876/TCP,443:30002/TCP,15443:32265/TCP   2m46s
|~ 💻
|
|--⫸  kubectl patch configmap/config-domain \                                                                                                                                  🔂
  --namespace knative-serving \
  --type merge \
  --patch '{"data":{"knative.runitoncloud.com":""}}'
configmap/config-domain patched
|~ 💻
|
|--⫸  kubectl get pods --namespace knative-serving                                                                                                                             🔂

NAME                               READY   STATUS    RESTARTS   AGE
activator-76984478f7-2trhj         1/1     Running   0          19m
autoscaler-598d974c99-p42h7        1/1     Running   0          19m
controller-9b998cd47-mbn2l         1/1     Running   0          19m
istio-webhook-69cd874949-nqh7f     1/1     Running   0          10m
networking-istio-df55795c6-n6tsb   1/1     Running   0          10m
webhook-658874f97-x8zd4            1/1     Running   0          19m
|~ 💻
|
|--⫸  cat <<EOF | kubectl apply -f -                                                                                                                                           🔂
pipe heredoc>
|~ 💻
|
|--⫸  cat <<EOF | kubectl apply -f -                                                                                                                                           🔂
pipe heredoc>
|~ 💻
|
|--⫸  ls -a                                                                                                                                                                    🔂
.                                      .istioctl                              .terraform.tfstate.lock.info           Pictures
..                                     .k9s                                   .terraform.versions                    Postman
.CFUserTextEncoding                    .kube                                  .tooling                               Public
.DS_Store                              .local                                 .viminfo                               bin
.Trash                                 .m2                                    .vscode                                community
.aws                                   .minikube                              .zcompdump-Aymen’s MacBook Pro-5.3     go
.azure                                 .mume                                  .zcompdump-Aymen’s MacBook Pro-5.7.1   istio-minimal-operator.yaml
.bash_history                          .mvnvm                                 .zprofile                              my-awesome-terminal
.bash_sessions                         .npm                                   .zsh_history                           project
.boto                                  .oh-my-zsh                             .zshrc                                 run-it-on-cloud
.config                                .oracle_jre_usage                      .zshrc.backup                          tcnf
.cups                                  .pylint.d                              AWSCLIV2.pkg                           terraform.tfstate
.dlv                                   .python_history                        Applications                           tmp.json
.docker                                .rediscli_history                      Desktop                                vue-theme-iterm2
.eclipse                               .shell.pre-oh-my-zsh                   Documents                              yunar
.editorconfig                          .skaffold                              Downloads                              zsh-syntax-highlighting
.gitconfig                             .ssh                                   Library
.gnupg                                 .terraform                             Movies
.helm                                  .terraform.d                           Music
|~ 💻
|
|--⫸  cd run-it-on-cloud/                                                                                                                                                      🔂
|~/run-it-on-cloud 💻
|
|--⫸  mkdir -p knative                                                                                                                                                         🔂
|~/run-it-on-cloud 💻
|
|--⫸  chmod -R 777 knative                                                                                                                                                     🔂
|~/run-it-on-cloud 💻
|
|--⫸  cd knative                                                                                                                                                               🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > helloworld.yaml                                                                                                                                             🔂
heredoc> apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
heredoc>
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > helloworld.yaml                                                                                                                                             🔂
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
heredoc>
heredoc>
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > helloworld.yaml                                                                                                                                             🔂
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
heredoc>
heredoc>
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./helloworld.yaml
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
EOF
kubect apply -f helloworld.yaml
zsh: command not found: kubect
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./helloworld.yaml
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
EOF
kubectl apply -f helloworld.yaml
service.serving.knative.dev/helloworld created
|~/run-it-on-cloud/knative 💻
|
|--⫸  k get svc                                                                                                                                                                🔂
NAME                       TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)                             AGE
helloworld-2vcx5           ClusterIP   10.0.117.219   <none>        80/TCP                              9s
helloworld-2vcx5-private   ClusterIP   10.0.179.157   <none>        80/TCP,9090/TCP,9091/TCP,8022/TCP   9s
kubernetes                 ClusterIP   10.0.0.1       <none>        443/TCP                             37m
|~/run-it-on-cloud/knative 💻
|
|--⫸  k get ksvc                                                                                                                                                               🔂
NAME         URL                                                  LATESTCREATED      LATESTREADY   READY     REASON
helloworld   http://helloworld.default.knative.runitoncloud.com   helloworld-2vcx5                 Unknown   RevisionMissing
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get ksvc                                                                                                                                                         🔂
NAME         URL                                                  LATESTCREATED      LATESTREADY        READY   REASON
helloworld   http://helloworld.default.knative.runitoncloud.com   helloworld-2vcx5   helloworld-2vcx5   True
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get service --namespace=istio-system knative-ingressgateway                                                                                                      🔂

Error from server (NotFound): services "knative-ingressgateway" not found
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get ksvc helloworld --output jsonpath='{.status.domain}'                                                                                                         🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl --namespace istio-system get service istio-ingressgateway                                                                                                        🔂

NAME                   TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)                                                      AGE
istio-ingressgateway   LoadBalancer   10.0.76.127   51.105.98.187   15021:30344/TCP,80:30876/TCP,443:30002/TCP,15443:32265/TCP   28m
|~/run-it-on-cloud/knative 💻
|
|--⫸  curl -H "Host: helloworld.default.runitoncloud.com" http://51.105.98.187                                                                                                 🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  curl -H "Host: helloworld.default.knative.runitoncloud.com" http://51.105.98.187                                                                                         🔂

Hello world!
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get pods                                                                                                                                     🔂
NAME                                           READY   STATUS    RESTARTS   AGE
helloworld-2vcx5-deployment-6b865d74f7-vs8pp   2/2     Running   0          29s
|~/run-it-on-cloud/knative 💻
|
|--⫸  curl -H "Host: helloworld.default.knative.runitoncloud.com" http://51.105.98.187                                                                     🔂

Hello world!
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get pods                                                                                                                                     🔂
NAME                                           READY   STATUS    RESTARTS   AGE
helloworld-2vcx5-deployment-6b865d74f7-vs8pp   2/2     Running   0          57s
|~/run-it-on-cloud/knative 💻
|
|--⫸  clear                                                                                                                                                🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get configuration,revision,route                                                                                                             🔂

NAME                                           LATESTCREATED      LATESTREADY        READY   REASON
configuration.serving.knative.dev/helloworld   helloworld-2vcx5   helloworld-2vcx5   True

NAME                                            CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
revision.serving.knative.dev/helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True

NAME                                   URL                                                  READY   REASON
route.serving.knative.dev/helloworld   http://helloworld.default.knative.runitoncloud.com   True
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./v1.yaml                                                                                                                               🔂
EOF
kubectl apply -f v1.yaml
error: no objects passed to apply
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./v1.yaml                                                                                                                               🔂
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: canary
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: gcr.io/knative-samples/knative-route-demo:blue
            env:
            - name: T_VERSION
              value: "blue"
EOF
kubectl apply -f v1.yaml
service.serving.knative.dev/canary created
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get revisions                                                                                                                                🔂

NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  curl -H "Host: canary.default.knative.runitoncloud.com" http://51.105.98.187                                                                         🔂

<!DOCTYPE html>
<html lang="en">
<head>
    <title>Knative Routing Demo</title>
    <link rel="stylesheet" type="text/css" href="/css/app.css" />
</head>
<body>

            <div class="blue">App v1</div>

    </div>
</body>
</html>%                                                                                                                                                      |~/run-it-on-cloud/knative 💻
|
|--⫸  cp v1.yaml v2.yaml                                                                                                                                   🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  vi v2.yaml                                                                                                                                           🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  k get revisions.serving.knative.dev                                                                                                                  🔂
NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  vi v2.yaml                                                                                                                                           🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  clear                                                                                                                                                🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl apply -f v2.yaml                                                                                                                             🔂

service.serving.knative.dev/canary configured
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get revisions                                                                                                                                🔂

NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY     REASON
canary-dwf4g       canary        canary-dwf4g       2            Unknown   Deploying
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get revisions                                                                                                                                🔂

NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
canary-dwf4g       canary        canary-dwf4g       2            True
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  vi v2.yaml                                                                                                                                           🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl apply -f v2.yaml                                                                                                                             🔂

service.serving.knative.dev/canary configured
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get revisions                                                                                                                                🔂

NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
canary-dwf4g       canary        canary-dwf4g       2            True
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  while true; do                                                                                                                                       🔂
  curl -s -H "Host: canary.default.knative.runitoncloud.com" http://51.105.98.187 | grep -E 'blue|green';
done
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
^C%                                                                                                                                                           |~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl describe route canary                                                                                                                        🔂

Name:         canary
Namespace:    default
Labels:       serving.knative.dev/service=canary
Annotations:  serving.knative.dev/creator: masterclient
              serving.knative.dev/lastModifier: masterclient
API Version:  serving.knative.dev/v1
Kind:         Route
Metadata:
  Creation Timestamp:  2020-07-20T22:43:15Z
  Finalizers:
    routes.serving.knative.dev
  Generation:  3
  Owner References:
    API Version:           serving.knative.dev/v1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  Service
    Name:                  canary
    UID:                   643af4d6-b50b-4b3f-b368-c76fdfeea237
  Resource Version:        129636
  Self Link:               /apis/serving.knative.dev/v1/namespaces/default/routes/canary
  UID:                     fd78deb4-3779-46cf-9b67-c3f893b64583
Spec:
  Traffic:
    Latest Revision:     false
    Percent:             80
    Revision Name:       canary-xnvvq
    Tag:                 current
    Latest Revision:     false
    Percent:             20
    Revision Name:       canary-dwf4g
    Tag:                 candidate
    Configuration Name:  canary
    Latest Revision:     true
    Tag:                 latest
Status:
  Address:
    URL:  http://canary.default.svc.cluster.local
  Conditions:
    Last Transition Time:  2020-07-20T22:52:49Z
    Status:                True
    Type:                  AllTrafficAssigned
    Last Transition Time:  2020-07-20T22:43:23Z
    Message:               autoTLS is not enabled
    Reason:                TLSNotEnabled
    Status:                True
    Type:                  CertificateProvisioned
    Last Transition Time:  2020-07-20T22:52:50Z
    Status:                True
    Type:                  IngressReady
    Last Transition Time:  2020-07-20T22:52:50Z
    Status:                True
    Type:                  Ready
  Observed Generation:     3
  Traffic:
    Latest Revision:  false
    Percent:          80
    Revision Name:    canary-xnvvq
    Tag:              current
    URL:              http://current-canary.default.knative.runitoncloud.com
    Latest Revision:  false
    Percent:          20
    Revision Name:    canary-dwf4g
    Tag:              candidate
    URL:              http://candidate-canary.default.knative.runitoncloud.com
    Latest Revision:  true
    Revision Name:    canary-dwf4g
    Tag:              latest
    URL:              http://latest-canary.default.knative.runitoncloud.com
  URL:                http://canary.default.knative.runitoncloud.com
Events:
  Type     Reason           Age                     From              Message
  ----     ------           ----                    ----              -------
  Normal   FinalizerUpdate  12m                     route-controller  Updated "canary" finalizers
  Normal   Created          11m                     route-controller  Created placeholder service "canary"
  Normal   Created          11m                     route-controller  Created Ingress "canary"
  Warning  InternalError    11m (x2 over 11m)       route-controller  failed to update Ingress: Operation cannot be fulfilled on ingresses.networking.internal.knative.dev "canary": the object has been modified; please apply your changes to the latest version and try again
  Warning  InternalError    3m32s (x15 over 4m32s)  route-controller  revision.serving.knative.dev "canary-00002" not found
  Normal   Created          2m27s                   route-controller  Created placeholder service "candidate-canary"
  Normal   Created          2m27s                   route-controller  Created placeholder service "current-canary"
  Normal   Created          2m27s                   route-controller  Created placeholder service "latest-canary"
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl apply -f v2.yaml                                                                                                                             🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  clear                                                                                                                                                🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./autoscale-go.yaml                                                                                                                     🔂
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: autoscale-go
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/autoscale-go:0.1"
EOF
kubectl apply -f autoscale-go.yaml
service.serving.knative.dev/autoscale-go created
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get ksvc                                                                                                                                     🔂
NAME           URL                                                    LATESTCREATED        LATESTREADY          READY   REASON
autoscale-go   http://autoscale-go.default.knative.runitoncloud.com   autoscale-go-sgf4k   autoscale-go-sgf4k   True
canary         http://canary.default.knative.runitoncloud.com         canary-dwf4g         canary-dwf4g         True
helloworld     http://helloworld.default.knative.runitoncloud.com     helloworld-2vcx5     helloworld-2vcx5     True
|~/run-it-on-cloud/knative 💻
|
|--⫸  IP_ADDRESS="$(kubectl get service knative-ingressgateway --namespace istio-system --output jsonpath="{.status.loadBalancer.ingress[*].ip}")"         🔂

Error from server (NotFound): services "knative-ingressgateway" not found
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get service --namespace=istio-system knative-ingressgateway                                                                                  🔂

Error from server (NotFound): services "knative-ingressgateway" not found
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get service --namespace=istio-system istio-ingressgateway                                                                                    🔂

NAME                   TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)                                                      AGE
istio-ingressgateway   LoadBalancer   10.0.76.127   51.105.98.187   15021:30344/TCP,80:30876/TCP,443:30002/TCP,15443:32265/TCP   57m
|~/run-it-on-cloud/knative 💻
|
|--⫸  IP_ADDRESS="$(kubectl get service --namespace=istio-system istio-ingressgateway --output jsonpath="{.status.loadBalancer.ingress[*].ip}")"           🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  echo $IP_ADDRESS                                                                                                                                     🔂
51.105.98.187
|~/run-it-on-cloud/knative 💻
|
|--⫸  curl --header "Host: autoscale-go.default.knative.runitoncloud.com" \                                                                                🔂
  "http://${IP_ADDRESS?}?sleep=1000"
Slept for 1001.77 milliseconds.
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl port-forward --namespace knative-monitoring \                                                                                                🔂
  $(kubectl get pods --namespace knative-monitoring \
      --selector=app=grafana --output=jsonpath="{.items..metadata.name}")\
  8080:3000
error: TYPE/NAME and list of ports are required for port-forward
See 'kubectl port-forward -h' for help and examples
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl port-forward -h                                                                                                                              🔂
Forward one or more local ports to a pod. This command requires the node to have 'socat' installed.

 Use resource type/name such as deployment/mydeployment to select a pod. Resource type defaults to 'pod' if omitted.

 If there are multiple pods matching the criteria, a pod will be selected automatically. The forwarding session ends
when the selected pod terminates, and rerun of the command is needed to resume forwarding.

Examples:
  # Listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 in the pod
  kubectl port-forward pod/mypod 5000 6000

  # Listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 in a pod selected by the
deployment
  kubectl port-forward deployment/mydeployment 5000 6000

  # Listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 in a pod selected by the service
  kubectl port-forward service/myservice 5000 6000

  # Listen on port 8888 locally, forwarding to 5000 in the pod
  kubectl port-forward pod/mypod 8888:5000

  # Listen on port 8888 on all addresses, forwarding to 5000 in the pod
  kubectl port-forward --address 0.0.0.0 pod/mypod 8888:5000

  # Listen on port 8888 on localhost and selected IP, forwarding to 5000 in the pod
  kubectl port-forward --address localhost,10.19.21.23 pod/mypod 8888:5000

  # Listen on a random port locally, forwarding to 5000 in the pod
  kubectl port-forward pod/mypod :5000

Options:
      --address=[localhost]: Addresses to listen on (comma separated). Only accepts IP addresses or localhost as a
value. When localhost is supplied, kubectl will try to bind on both 127.0.0.1 and ::1 and will fail if neither of these
addresses are available to bind.
      --pod-running-timeout=1m0s: The length of time (like 5s, 2m, or 3h, higher than zero) to wait until at least one
pod is running

Usage:
  kubectl port-forward TYPE/NAME [options] [LOCAL_PORT:]REMOTE_PORT [...[LOCAL_PORT_N:]REMOTE_PORT_N]

Use "kubectl options" for a list of global command-line options (applies to all commands).
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl port-forward --namespace knative-monitoring \                                                                                                🔂
  $(kubectl get pods --namespace knative-monitoring \
      --selector=app=grafana --output=jsonpath="{.items..metadata.name}")\
  8080:3000
error: TYPE/NAME and list of ports are required for port-forward
See 'kubectl port-forward -h' for help and examples
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl port-forward --namespace knative-monitoring 8080:3000 \                                                                                      🔂
  $(kubectl get pods --namespace knative-monitoring \
      --selector=app=grafana --output=jsonpath="{.items..metadata.name}")\

error: TYPE/NAME and list of ports are required for port-forward
See 'kubectl port-forward -h' for help and examples
|~/run-it-on-cloud/knative 💻
|
|--⫸  go get github.com/rakyll/hey                                                                                                                         🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  hey -host autoscale-go.default.knative.runitoncloud.com -c 500 -n 150000 \                                                                           🔂
  "http://${IP_ADDRESS?}?sleep=1000"
^C
Summary:
  Total:	185.3560 secs
  Slowest:	3.7445 secs
  Fastest:	1.0209 secs
  Average:	1.1032 secs
  Requests/sec:	632.6422

  Total data:	1333248 bytes
  Size/request:	32 bytes

Response time histogram:
  1.021 [1]	|
  1.293 [41341]	|■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■
  1.566 [74]	|
  1.838 [0]	|
  2.110 [0]	|
  2.383 [0]	|
  2.655 [0]	|
  2.927 [0]	|
  3.200 [0]	|
  3.472 [0]	|
  3.744 [248]	|


Latency distribution:
  10% in 1.0332 secs
  25% in 1.0505 secs
  50% in 1.0875 secs
  75% in 1.1253 secs
  90% in 1.1294 secs
  95% in 1.1320 secs
  99% in 1.2075 secs

Details (average, fastest, slowest):
  DNS+dialup:	0.0005 secs, 1.0209 secs, 3.7445 secs
  DNS-lookup:	0.0000 secs, 0.0000 secs, 0.0000 secs
  req write:	0.0000 secs, 0.0000 secs, 0.0713 secs
  resp wait:	1.1019 secs, 1.0208 secs, 3.6778 secs
  resp read:	0.0006 secs, 0.0000 secs, 0.0532 secs

Status code distribution:
  [200]	41664 responses

Error distribution:
  [75600]	Get "http://51.105.98.187?sleep=1000": dial tcp 51.105.98.187:80: socket: too many open files

|~/run-it-on-cloud/knative 💻
|
|--⫸                                                                                                                                                       🔂
````
`|--⫸  az group create -l westus -n runItOnCloud                                                                                                                                                          🔂
|~ 💻
|
|--⫸  az aks create \                                                                                                                                                                                    🔂
    --resource-group runitoncloud-tf \
    --name runitonCloud \
    --node-count 2 \
    --generate-ssh-keys \
    --attach-acr runitoncloud
{- Finished ..
  "aadProfile": null,
  "addonProfiles": {
    "KubeDashboard": {
      "config": null,
      "enabled": true,
      "identity": null
    }
  },
  "agentPoolProfiles": [
    {
      "availabilityZones": null,
      "count": 2,
      "enableAutoScaling": null,
      "enableNodePublicIp": false,
      "maxCount": null,
      "maxPods": 110,
      "minCount": null,
      "mode": "System",
      "name": "nodepool1",
      "nodeLabels": {},
      "nodeTaints": null,
      "orchestratorVersion": "1.16.10",
      "osDiskSizeGb": 128,
      "osType": "Linux",
      "provisioningState": "Succeeded",
      "scaleSetEvictionPolicy": null,
      "scaleSetPriority": null,
      "spotMaxPrice": null,
      "tags": null,
      "type": "VirtualMachineScaleSets",
      "vmSize": "Standard_DS2_v2",
      "vnetSubnetId": null
    }
  ],
  "apiServerAccessProfile": null,
  "autoScalerProfile": null,
  "diskEncryptionSetId": null,
  "dnsPrefix": "runitonClo-runitoncloud-tf-d03598",
  "enablePodSecurityPolicy": null,
  "enableRbac": true,
  "fqdn": "runitonclo-runitoncloud-tf-d03598-727b6814.hcp.westeurope.azmk8s.io",
  "id": "/subscriptions/d0359825-dc9e-4f37-b195-2e5148b4923e/resourcegroups/runitoncloud-tf/providers/Microsoft.ContainerService/managedClusters/runitonCloud",
  "identity": null,
  "identityProfile": null,
  "kubernetesVersion": "1.16.10",
  "linuxProfile": {
    "adminUsername": "azureuser",
    "ssh": {
      "publicKeys": [
        {
          "keyData": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCwcpcdKVemN639FwzKdEz/BjlkmsEDeQTOB5zZ0cpH+ZQwMB5N4Fkk+StqjskeSV9Tn6ZW3MiMPB94aXOIrIuC2GU5B9L5bEplB9PjUxzr9pxTaDCnPXHaRIbElDEUV0BsJywf3cAyO6rhA1kcLfOj3ZoSSmq4XcvRVqITDWJNUfteWTKySMKRdMfeQQj1UO4SSGg9p+HqcaWn7K87Oz8wWAS7M5Z+2+zV9U4AhE0qqkTJtADqd1IzXPnvedxfnMOa9m7leg2812I73l70iuQzB8Gmab+WjGS6SLI2zC61cGViXMWvHqEujns9W4atyWXTeXiwx+mbPVkF3sJBSJyf aymensegni@Aymens-MBP.fritz.box\n"
        }
      ]
    }
  },
  "location": "westeurope",
  "maxAgentPools": 10,
  "name": "runitonCloud",
  "networkProfile": {
    "dnsServiceIp": "10.0.0.10",
    "dockerBridgeCidr": "172.17.0.1/16",
    "loadBalancerProfile": {
      "allocatedOutboundPorts": null,
      "effectiveOutboundIps": [
        {
          "id": "/subscriptions/d0359825-dc9e-4f37-b195-2e5148b4923e/resourceGroups/MC_runitoncloud-tf_runitonCloud_westeurope/providers/Microsoft.Network/publicIPAddresses/c7839e72-4db8-46f4-9707-addc84618111",
          "resourceGroup": "MC_runitoncloud-tf_runitonCloud_westeurope"
        }
      ],
      "idleTimeoutInMinutes": null,
      "managedOutboundIps": {
        "count": 1
      },
      "outboundIpPrefixes": null,
      "outboundIps": null
    },
    "loadBalancerSku": "Standard",
    "networkMode": null,
    "networkPlugin": "kubenet",
    "networkPolicy": null,
    "outboundType": "loadBalancer",
    "podCidr": "10.244.0.0/16",
    "serviceCidr": "10.0.0.0/16"
  },
  "nodeResourceGroup": "MC_runitoncloud-tf_runitonCloud_westeurope",
  "privateFqdn": null,
  "provisioningState": "Succeeded",
  "resourceGroup": "runitoncloud-tf",
  "servicePrincipalProfile": {
    "clientId": "8f71ebe6-4635-4d38-b766-a771e40b3504",
    "secret": null
  },
  "sku": {
    "name": "Basic",
    "tier": "Free"
  },
  "tags": null,
  "type": "Microsoft.ContainerService/ManagedClusters",
  "windowsProfile": null
}
|~ 💻
|
|--⫸  az aks get-credentials --resource-group runitoncloud-tf --name runitonCloud                                                                                                                        🔂
Merged "runitonCloud" as current context in /Users/aymensegni/.kube/config
|~ 💻
|
|--⫸  k get nodes                                                                                                                                                                                        🔂
NAME                                STATUS   ROLES   AGE   VERSION
aks-nodepool1-57319200-vmss000000   Ready    agent   96s   v1.16.10
aks-nodepool1-57319200-vmss000001   Ready    agent   87s   v1.16.10
|~ 💻
|
|--⫸  kubectl apply --filename https://github.com/knative/serving/releases/download/v0.16.0/serving-crds.yaml                                                                                            🔂

customresourcedefinition.apiextensions.k8s.io/certificates.networking.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/configurations.serving.knative.dev created
customresourcedefinition.apiextensions.k8s.io/ingresses.networking.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/metrics.autoscaling.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/podautoscalers.autoscaling.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/revisions.serving.knative.dev created
customresourcedefinition.apiextensions.k8s.io/routes.serving.knative.dev created
customresourcedefinition.apiextensions.k8s.io/serverlessservices.networking.internal.knative.dev created
customresourcedefinition.apiextensions.k8s.io/services.serving.knative.dev created
customresourcedefinition.apiextensions.k8s.io/images.caching.internal.knative.dev created
|~ 💻
|
|--⫸  kubectl apply --filename https://github.com/knative/serving/releases/download/v0.16.0/serving-core.yaml                                                                                            🔂

customresourcedefinition.apiextensions.k8s.io/images.caching.internal.knative.dev unchanged
namespace/knative-serving created
serviceaccount/controller created
clusterrole.rbac.authorization.k8s.io/knative-serving-admin created
clusterrolebinding.rbac.authorization.k8s.io/knative-serving-controller-admin created
image.caching.internal.knative.dev/queue-proxy created
configmap/config-autoscaler created
configmap/config-defaults created
configmap/config-deployment created
configmap/config-domain created
configmap/config-features created
configmap/config-gc created
configmap/config-leader-election created
configmap/config-logging created
configmap/config-network created
configmap/config-observability created
configmap/config-tracing created
horizontalpodautoscaler.autoscaling/activator created
deployment.apps/activator created
service/activator-service created
deployment.apps/autoscaler created
service/autoscaler created
deployment.apps/controller created
service/controller created
deployment.apps/webhook created
service/webhook created
customresourcedefinition.apiextensions.k8s.io/certificates.networking.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/configurations.serving.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/ingresses.networking.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/metrics.autoscaling.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/podautoscalers.autoscaling.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/revisions.serving.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/routes.serving.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/serverlessservices.networking.internal.knative.dev unchanged
customresourcedefinition.apiextensions.k8s.io/services.serving.knative.dev unchanged
clusterrole.rbac.authorization.k8s.io/knative-serving-addressable-resolver created
clusterrole.rbac.authorization.k8s.io/knative-serving-namespaced-admin created
clusterrole.rbac.authorization.k8s.io/knative-serving-namespaced-edit created
clusterrole.rbac.authorization.k8s.io/knative-serving-namespaced-view created
clusterrole.rbac.authorization.k8s.io/knative-serving-core created
clusterrole.rbac.authorization.k8s.io/knative-serving-podspecable-binding created
validatingwebhookconfiguration.admissionregistration.k8s.io/config.webhook.serving.knative.dev created
mutatingwebhookconfiguration.admissionregistration.k8s.io/webhook.serving.knative.dev created
validatingwebhookconfiguration.admissionregistration.k8s.io/validation.webhook.serving.knative.dev created
secret/webhook-certs created
|~ 💻
|
|--⫸  cat << EOF > ./istio-minimal-operator.yaml                                                                                                                                                         🔂
apiVersion: install.istio.io/v1alpha1
kind: IstioOperator
spec:
  values:
    global:
      proxy:
        autoInject: disabled
      useMCP: false
      # The third-party-jwt is not enabled on all k8s.
      # See: https://istio.io/docs/ops/best-practices/security/\#configure-third-party-service-account-tokens
      jwtPolicy: first-party-jwt

  addonComponents:
    pilot:
      enabled: true
    prometheus:
      enabled: false

  components:
    ingressGateways:
      - name: istio-ingressgateway
        enabled: true
      - name: cluster-local-gateway
        enabled: true
        label:
          istio: cluster-local-gateway
          app: cluster-local-gateway
        k8s:
          service:
            type: ClusterIP
            ports:
            - port: 15020
              name: status-port
            - port: 80
              name: http2
            - port: 443
              name: https
EOF

istioctl manifest apply -f istio-minimal-operator.yaml
zsh: command not found: istioctl
|~ 💻
|
|--⫸  curl -sL https://istio.io/downloadIstioctl | sh -                                                                                                                                                  🔂

Downloading istioctl-1.6.5 from https://github.com/istio/istio/releases/download/1.6.5/istioctl-1.6.5-osx.tar.gz ...
istioctl-1.6.5-osx.tar.gz download complete!

Add the istioctl to your path with:
  export PATH=$PATH:$HOME/.istioctl/bin

Begin the Istio pre-installation verification check by running:
	 istioctl verify-install

Need more information? Visit https://istio.io/docs/reference/commands/istioctl/
|~ 💻
|
|--⫸  export PATH=$PATH:$HOME/.istioctl/bin                                                                                                                                                              🔂

|~ 💻
|
|--⫸  cat << EOF > ./istio-minimal-operator.yaml                                                                                                                                                         🔂
apiVersion: install.istio.io/v1alpha1
kind: IstioOperator
spec:
  values:
    global:
      proxy:
        autoInject: disabled
      useMCP: false
      # The third-party-jwt is not enabled on all k8s.
      # See: https://istio.io/docs/ops/best-practices/security/\#configure-third-party-service-account-tokens
      jwtPolicy: first-party-jwt

  addonComponents:
    pilot:
      enabled: true
    prometheus:
      enabled: false

  components:
    ingressGateways:
      - name: istio-ingressgateway
        enabled: true
      - name: cluster-local-gateway
        enabled: true
        label:
          istio: cluster-local-gateway
          app: cluster-local-gateway
        k8s:
          service:
            type: ClusterIP
            ports:
            - port: 15020
              name: status-port
            - port: 80
              name: http2
            - port: 443
              name: https
EOF

istioctl manifest apply -f istio-minimal-operator.yaml
✔ Istio core installed
✔ Istiod installed
✔ Ingress gateways installed
✔ Addons installed
✔ Installation complete                                                                                                                                                           |~ 💻
|
|--⫸  kubectl label namespace knative-serving istio-injection=enabled                                                                                                          🔂

namespace/knative-serving labeled
|~ 💻
|
|--⫸  cat <<EOF | kubectl apply -f -                                                                                                                                           🔂
apiVersion: "security.istio.io/v1beta1"
kind: "PeerAuthentication"
metadata:
  name: "default"
  namespace: "knative-serving"
spec:
  mtls:
    mode: PERMISSIVE
EOF
peerauthentication.security.istio.io/default created
|~ 💻
|
|--⫸  kubectl apply --filename https://github.com/knative/net-istio/releases/download/v0.16.0/release.yaml                                                                     🔂

clusterrole.rbac.authorization.k8s.io/knative-serving-istio created
gateway.networking.istio.io/knative-ingress-gateway created
gateway.networking.istio.io/cluster-local-gateway created
mutatingwebhookconfiguration.admissionregistration.k8s.io/webhook.istio.networking.internal.knative.dev created
validatingwebhookconfiguration.admissionregistration.k8s.io/config.webhook.istio.networking.internal.knative.dev created
secret/istio-webhook-certs created
configmap/config-istio created
deployment.apps/networking-istio created
deployment.apps/istio-webhook created
service/istio-webhook created
|~ 💻
|
|--⫸  kubectl --namespace istio-system get service istio-ingressgateway                                                                                                        🔂

NAME                   TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)                                                      AGE
istio-ingressgateway   LoadBalancer   10.0.76.127   51.105.98.187   15021:30344/TCP,80:30876/TCP,443:30002/TCP,15443:32265/TCP   2m46s
|~ 💻
|
|--⫸  kubectl patch configmap/config-domain \                                                                                                                                  🔂
  --namespace knative-serving \
  --type merge \
  --patch '{"data":{"knative.runitoncloud.com":""}}'
configmap/config-domain patched
|~ 💻
|
|--⫸  kubectl get pods --namespace knative-serving                                                                                                                             🔂

NAME                               READY   STATUS    RESTARTS   AGE
activator-76984478f7-2trhj         1/1     Running   0          19m
autoscaler-598d974c99-p42h7        1/1     Running   0          19m
controller-9b998cd47-mbn2l         1/1     Running   0          19m
istio-webhook-69cd874949-nqh7f     1/1     Running   0          10m
networking-istio-df55795c6-n6tsb   1/1     Running   0          10m
webhook-658874f97-x8zd4            1/1     Running   0          19m
|~ 💻
|
|--⫸  cat <<EOF | kubectl apply -f -                                                                                                                                           🔂
pipe heredoc>
|~ 💻
|
|--⫸  cat <<EOF | kubectl apply -f -                                                                                                                                           🔂
pipe heredoc>
|~ 💻
|
|--⫸  ls -a                                                                                                                                                                    🔂
.                                      .istioctl                              .terraform.tfstate.lock.info           Pictures
..                                     .k9s                                   .terraform.versions                    Postman
.CFUserTextEncoding                    .kube                                  .tooling                               Public
.DS_Store                              .local                                 .viminfo                               bin
.Trash                                 .m2                                    .vscode                                community
.aws                                   .minikube                              .zcompdump-Aymen’s MacBook Pro-5.3     go
.azure                                 .mume                                  .zcompdump-Aymen’s MacBook Pro-5.7.1   istio-minimal-operator.yaml
.bash_history                          .mvnvm                                 .zprofile                              my-awesome-terminal
.bash_sessions                         .npm                                   .zsh_history                           project
.boto                                  .oh-my-zsh                             .zshrc                                 run-it-on-cloud
.config                                .oracle_jre_usage                      .zshrc.backup                          tcnf
.cups                                  .pylint.d                              AWSCLIV2.pkg                           terraform.tfstate
.dlv                                   .python_history                        Applications                           tmp.json
.docker                                .rediscli_history                      Desktop                                vue-theme-iterm2
.eclipse                               .shell.pre-oh-my-zsh                   Documents                              yunar
.editorconfig                          .skaffold                              Downloads                              zsh-syntax-highlighting
.gitconfig                             .ssh                                   Library
.gnupg                                 .terraform                             Movies
.helm                                  .terraform.d                           Music
|~ 💻
|
|--⫸  cd run-it-on-cloud/                                                                                                                                                      🔂
|~/run-it-on-cloud 💻
|
|--⫸  mkdir -p knative                                                                                                                                                         🔂
|~/run-it-on-cloud 💻
|
|--⫸  chmod -R 777 knative                                                                                                                                                     🔂
|~/run-it-on-cloud 💻
|
|--⫸  cd knative                                                                                                                                                               🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > helloworld.yaml                                                                                                                                             🔂
heredoc> apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
heredoc>
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > helloworld.yaml                                                                                                                                             🔂
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
heredoc>
heredoc>
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > helloworld.yaml                                                                                                                                             🔂
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
heredoc>
heredoc>
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./helloworld.yaml
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
EOF
kubect apply -f helloworld.yaml
zsh: command not found: kubect
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./helloworld.yaml
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: "helloworld"
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/helloworld-go"
            env:
              - name: "TARGET"
                value: "world"
EOF
kubectl apply -f helloworld.yaml
service.serving.knative.dev/helloworld created
|~/run-it-on-cloud/knative 💻
|
|--⫸  k get svc                                                                                                                                                                🔂
NAME                       TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)                             AGE
helloworld-2vcx5           ClusterIP   10.0.117.219   <none>        80/TCP                              9s
helloworld-2vcx5-private   ClusterIP   10.0.179.157   <none>        80/TCP,9090/TCP,9091/TCP,8022/TCP   9s
kubernetes                 ClusterIP   10.0.0.1       <none>        443/TCP                             37m
|~/run-it-on-cloud/knative 💻
|
|--⫸  k get ksvc                                                                                                                                                               🔂
NAME         URL                                                  LATESTCREATED      LATESTREADY   READY     REASON
helloworld   http://helloworld.default.knative.runitoncloud.com   helloworld-2vcx5                 Unknown   RevisionMissing
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get ksvc                                                                                                                                                         🔂
NAME         URL                                                  LATESTCREATED      LATESTREADY        READY   REASON
helloworld   http://helloworld.default.knative.runitoncloud.com   helloworld-2vcx5   helloworld-2vcx5   True
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get service --namespace=istio-system knative-ingressgateway                                                                                                      🔂

Error from server (NotFound): services "knative-ingressgateway" not found
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get ksvc helloworld --output jsonpath='{.status.domain}'                                                                                                         🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl --namespace istio-system get service istio-ingressgateway                                                                                                        🔂

NAME                   TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)                                                      AGE
istio-ingressgateway   LoadBalancer   10.0.76.127   51.105.98.187   15021:30344/TCP,80:30876/TCP,443:30002/TCP,15443:32265/TCP   28m
|~/run-it-on-cloud/knative 💻
|
|--⫸  curl -H "Host: helloworld.default.runitoncloud.com" http://51.105.98.187                                                                                                 🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  curl -H "Host: helloworld.default.knative.runitoncloud.com" http://51.105.98.187                                                                                         🔂

Hello world!
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get pods                                                                                                                                     🔂
NAME                                           READY   STATUS    RESTARTS   AGE
helloworld-2vcx5-deployment-6b865d74f7-vs8pp   2/2     Running   0          29s
|~/run-it-on-cloud/knative 💻
|
|--⫸  curl -H "Host: helloworld.default.knative.runitoncloud.com" http://51.105.98.187                                                                     🔂

Hello world!
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get pods                                                                                                                                     🔂
NAME                                           READY   STATUS    RESTARTS   AGE
helloworld-2vcx5-deployment-6b865d74f7-vs8pp   2/2     Running   0          57s
|~/run-it-on-cloud/knative 💻
|
|--⫸  clear                                                                                                                                                🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get configuration,revision,route                                                                                                             🔂

NAME                                           LATESTCREATED      LATESTREADY        READY   REASON
configuration.serving.knative.dev/helloworld   helloworld-2vcx5   helloworld-2vcx5   True

NAME                                            CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
revision.serving.knative.dev/helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True

NAME                                   URL                                                  READY   REASON
route.serving.knative.dev/helloworld   http://helloworld.default.knative.runitoncloud.com   True
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./v1.yaml                                                                                                                               🔂
EOF
kubectl apply -f v1.yaml
error: no objects passed to apply
|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./v1.yaml                                                                                                                               🔂
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: canary
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: gcr.io/knative-samples/knative-route-demo:blue
            env:
            - name: T_VERSION
              value: "blue"
EOF
kubectl apply -f v1.yaml
service.serving.knative.dev/canary created
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get revisions                                                                                                                                🔂

NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  curl -H "Host: canary.default.knative.runitoncloud.com" http://51.105.98.187                                                                         🔂

<!DOCTYPE html>
<html lang="en">
<head>
    <title>Knative Routing Demo</title>
    <link rel="stylesheet" type="text/css" href="/css/app.css" />
</head>
<body>

            <div class="blue">App v1</div>

    </div>
</body>
</html>%                                                                                                                                                      |~/run-it-on-cloud/knative 💻
|
|--⫸  cp v1.yaml v2.yaml                                                                                                                                   🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  vi v2.yaml                                                                                                                                           🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  k get revisions.serving.knative.dev                                                                                                                  🔂
NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  vi v2.yaml                                                                                                                                           🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  clear                                                                                                                                                🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl apply -f v2.yaml                                                                                                                             🔂

service.serving.knative.dev/canary configured
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get revisions                                                                                                                                🔂

NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY     REASON
canary-dwf4g       canary        canary-dwf4g       2            Unknown   Deploying
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get revisions                                                                                                                                🔂

NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
canary-dwf4g       canary        canary-dwf4g       2            True
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  vi v2.yaml                                                                                                                                           🔂
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl apply -f v2.yaml                                                                                                                             🔂

service.serving.knative.dev/canary configured
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get revisions                                                                                                                                🔂

NAME               CONFIG NAME   K8S SERVICE NAME   GENERATION   READY   REASON
canary-dwf4g       canary        canary-dwf4g       2            True
canary-xnvvq       canary        canary-xnvvq       1            True
helloworld-2vcx5   helloworld    helloworld-2vcx5   1            True
|~/run-it-on-cloud/knative 💻
|
|--⫸  while true; do                                                                                                                                       🔂
  curl -s -H "Host: canary.default.knative.runitoncloud.com" http://51.105.98.187 | grep -E 'blue|green';
done
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
            <div class="green">App v2</div>
            <div class="blue">App v1</div>
            <div class="blue">App v1</div>
^C%                                                                                                                                                           |~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl describe route canary                                                                                                                        🔂

Name:         canary
Namespace:    default
Labels:       serving.knative.dev/service=canary
Annotations:  serving.knative.dev/creator: masterclient
              serving.knative.dev/lastModifier: masterclient
API Version:  serving.knative.dev/v1
Kind:         Route
Metadata:
  Creation Timestamp:  2020-07-20T22:43:15Z
  Finalizers:
    routes.serving.knative.dev
  Generation:  3
  Owner References:
    API Version:           serving.knative.dev/v1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  Service
    Name:                  canary
    UID:                   643af4d6-b50b-4b3f-b368-c76fdfeea237
  Resource Version:        129636
  Self Link:               /apis/serving.knative.dev/v1/namespaces/default/routes/canary
  UID:                     fd78deb4-3779-46cf-9b67-c3f893b64583
Spec:
  Traffic:
    Latest Revision:     false
    Percent:             80
    Revision Name:       canary-xnvvq
    Tag:                 current
    Latest Revision:     false
    Percent:             20
    Revision Name:       canary-dwf4g
    Tag:                 candidate
    Configuration Name:  canary
    Latest Revision:     true
    Tag:                 latest
Status:
  Address:
    URL:  http://canary.default.svc.cluster.local
  Conditions:
    Last Transition Time:  2020-07-20T22:52:49Z
    Status:                True
    Type:                  AllTrafficAssigned
    Last Transition Time:  2020-07-20T22:43:23Z
    Message:               autoTLS is not enabled
    Reason:                TLSNotEnabled
    Status:                True
    Type:                  CertificateProvisioned
    Last Transition Time:  2020-07-20T22:52:50Z
    Status:                True
    Type:                  IngressReady
    Last Transition Time:  2020-07-20T22:52:50Z
    Status:                True
    Type:                  Ready
  Observed Generation:     3
  Traffic:
    Latest Revision:  false
    Percent:          80
    Revision Name:    canary-xnvvq
    Tag:              current
    URL:              http://current-canary.default.knative.runitoncloud.com
    Latest Revision:  false
    Percent:          20
    Revision Name:    canary-dwf4g
    Tag:              candidate
    URL:              http://candidate-canary.default.knative.runitoncloud.com
    Latest Revision:  true
    Revision Name:    canary-dwf4g
    Tag:              latest
    URL:              http://latest-canary.default.knative.runitoncloud.com
  URL:                http://canary.default.knative.runitoncloud.com
Events:
  Type     Reason           Age                     From              Message
  ----     ------           ----                    ----              -------
  Normal   FinalizerUpdate  12m                     route-controller  Updated "canary" finalizers
  Normal   Created          11m                     route-controller  Created placeholder service "canary"
  Normal   Created          11m                     route-controller  Created Ingress "canary"
  Warning  InternalError    11m (x2 over 11m)       route-controller  failed to update Ingress: Operation cannot be fulfilled on ingresses.networking.internal.knative.dev "canary": the object has been modified; please apply your changes to the latest version and try again
  Warning  InternalError    3m32s (x15 over 4m32s)  route-controller  revision.serving.knative.dev "canary-00002" not found
  Normal   Created          2m27s                   route-controller  Created placeholder service "candidate-canary"
  Normal   Created          2m27s                   route-controller  Created placeholder service "current-canary"
  Normal   Created          2m27s                   route-controller  Created placeholder service "latest-canary"
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl apply -f v2.yaml                                                                                                                             🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  clear                                                                                                                                                🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  cat << EOF > ./autoscale-go.yaml                                                                                                                     🔂
apiVersion: serving.knative.dev/v1alpha1
kind: Service
metadata:
  name: autoscale-go
spec:
  runLatest:
    configuration:
      revisionTemplate:
        spec:
          container:
            image: "gcr.io/knative-samples/autoscale-go:0.1"
EOF
kubectl apply -f autoscale-go.yaml
service.serving.knative.dev/autoscale-go created
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get ksvc                                                                                                                                     🔂
NAME           URL                                                    LATESTCREATED        LATESTREADY          READY   REASON
autoscale-go   http://autoscale-go.default.knative.runitoncloud.com   autoscale-go-sgf4k   autoscale-go-sgf4k   True
canary         http://canary.default.knative.runitoncloud.com         canary-dwf4g         canary-dwf4g         True
helloworld     http://helloworld.default.knative.runitoncloud.com     helloworld-2vcx5     helloworld-2vcx5     True
|~/run-it-on-cloud/knative 💻
|
|--⫸  IP_ADDRESS="$(kubectl get service knative-ingressgateway --namespace istio-system --output jsonpath="{.status.loadBalancer.ingress[*].ip}")"         🔂

Error from server (NotFound): services "knative-ingressgateway" not found
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get service --namespace=istio-system knative-ingressgateway                                                                                  🔂

Error from server (NotFound): services "knative-ingressgateway" not found
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl get service --namespace=istio-system istio-ingressgateway                                                                                    🔂

NAME                   TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)                                                      AGE
istio-ingressgateway   LoadBalancer   10.0.76.127   51.105.98.187   15021:30344/TCP,80:30876/TCP,443:30002/TCP,15443:32265/TCP   57m
|~/run-it-on-cloud/knative 💻
|
|--⫸  IP_ADDRESS="$(kubectl get service --namespace=istio-system istio-ingressgateway --output jsonpath="{.status.loadBalancer.ingress[*].ip}")"           🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  echo $IP_ADDRESS                                                                                                                                     🔂
51.105.98.187
|~/run-it-on-cloud/knative 💻
|
|--⫸  curl --header "Host: autoscale-go.default.knative.runitoncloud.com" \                                                                                🔂
  "http://${IP_ADDRESS?}?sleep=1000"
Slept for 1001.77 milliseconds.
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl port-forward --namespace knative-monitoring \                                                                                                🔂
  $(kubectl get pods --namespace knative-monitoring \
      --selector=app=grafana --output=jsonpath="{.items..metadata.name}")\
  8080:3000
error: TYPE/NAME and list of ports are required for port-forward
See 'kubectl port-forward -h' for help and examples
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl port-forward -h                                                                                                                              🔂
Forward one or more local ports to a pod. This command requires the node to have 'socat' installed.

 Use resource type/name such as deployment/mydeployment to select a pod. Resource type defaults to 'pod' if omitted.

 If there are multiple pods matching the criteria, a pod will be selected automatically. The forwarding session ends
when the selected pod terminates, and rerun of the command is needed to resume forwarding.

Examples:
  # Listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 in the pod
  kubectl port-forward pod/mypod 5000 6000

  # Listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 in a pod selected by the
deployment
  kubectl port-forward deployment/mydeployment 5000 6000

  # Listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 in a pod selected by the service
  kubectl port-forward service/myservice 5000 6000

  # Listen on port 8888 locally, forwarding to 5000 in the pod
  kubectl port-forward pod/mypod 8888:5000

  # Listen on port 8888 on all addresses, forwarding to 5000 in the pod
  kubectl port-forward --address 0.0.0.0 pod/mypod 8888:5000

  # Listen on port 8888 on localhost and selected IP, forwarding to 5000 in the pod
  kubectl port-forward --address localhost,10.19.21.23 pod/mypod 8888:5000

  # Listen on a random port locally, forwarding to 5000 in the pod
  kubectl port-forward pod/mypod :5000

Options:
      --address=[localhost]: Addresses to listen on (comma separated). Only accepts IP addresses or localhost as a
value. When localhost is supplied, kubectl will try to bind on both 127.0.0.1 and ::1 and will fail if neither of these
addresses are available to bind.
      --pod-running-timeout=1m0s: The length of time (like 5s, 2m, or 3h, higher than zero) to wait until at least one
pod is running

Usage:
  kubectl port-forward TYPE/NAME [options] [LOCAL_PORT:]REMOTE_PORT [...[LOCAL_PORT_N:]REMOTE_PORT_N]

Use "kubectl options" for a list of global command-line options (applies to all commands).
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl port-forward --namespace knative-monitoring \                                                                                                🔂
  $(kubectl get pods --namespace knative-monitoring \
      --selector=app=grafana --output=jsonpath="{.items..metadata.name}")\
  8080:3000
error: TYPE/NAME and list of ports are required for port-forward
See 'kubectl port-forward -h' for help and examples
|~/run-it-on-cloud/knative 💻
|
|--⫸  kubectl port-forward --namespace knative-monitoring 8080:3000 \                                                                                      🔂
  $(kubectl get pods --namespace knative-monitoring \
      --selector=app=grafana --output=jsonpath="{.items..metadata.name}")\

error: TYPE/NAME and list of ports are required for port-forward
See 'kubectl port-forward -h' for help and examples
|~/run-it-on-cloud/knative 💻
|
|--⫸  go get github.com/rakyll/hey                                                                                                                         🔂

|~/run-it-on-cloud/knative 💻
|
|--⫸  hey -host autoscale-go.default.knative.runitoncloud.com -c 500 -n 150000 \                                                                           🔂
  "http://${IP_ADDRESS?}?sleep=1000"
^C
Summary:
  Total:	185.3560 secs
  Slowest:	3.7445 secs
  Fastest:	1.0209 secs
  Average:	1.1032 secs
  Requests/sec:	632.6422

  Total data:	1333248 bytes
  Size/request:	32 bytes

Response time histogram:
  1.021 [1]	|
  1.293 [41341]	|■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■
  1.566 [74]	|
  1.838 [0]	|
  2.110 [0]	|
  2.383 [0]	|
  2.655 [0]	|
  2.927 [0]	|
  3.200 [0]	|
  3.472 [0]	|
  3.744 [248]	|


Latency distribution:
  10% in 1.0332 secs
  25% in 1.0505 secs
  50% in 1.0875 secs
  75% in 1.1253 secs
  90% in 1.1294 secs
  95% in 1.1320 secs
  99% in 1.2075 secs

Details (average, fastest, slowest):
  DNS+dialup:	0.0005 secs, 1.0209 secs, 3.7445 secs
  DNS-lookup:	0.0000 secs, 0.0000 secs, 0.0000 secs
  req write:	0.0000 secs, 0.0000 secs, 0.0713 secs
  resp wait:	1.1019 secs, 1.0208 secs, 3.6778 secs
  resp read:	0.0006 secs, 0.0000 secs, 0.0532 secs

Status code distribution:
  [200]	41664 responses

Error distribution:
  [75600]	Get "http://51.105.98.187?sleep=1000": dial tcp 51.105.98.187:80: socket: too many open files

|~/run-it-on-cloud/knative 💻
|
|--⫸                                                                                                                                                       🔂
```
