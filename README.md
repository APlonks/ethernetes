# Ethernetes

## Prerequisites

In /etc/hosts or in DNS add
```
<IP> ether-faucet
```

### Configure Kubernetes Dashboard
```bash
microk8s enable dashboard

microk8s kubectl create token default

microk8s kubectl port-forward -n kube-system service/kubernetes-dashboard 10443:443

# Then port forward 10443 in vscode access it to http://localhost:10443
```

### Configure Ingress
```bash
microk8s enable dashboard
```

### Configure DNS 
```bash
microk8s enable dns
```

Verify the pod is working : 
```bash
microk8s kubectl get pods -n kube-system
```

Open a shell in a busybox : 
```bash
microk8s kubectl run -it --rm --restart=Never dns-test --image=busybox -- sh
```

Test a service configured in the cluster :
```bash
nslookup geth-bootnode-svc
```

## RUN and STOP

git clone 

### Run the chart :

microk8s.helm install ethernetes-chart ethernetes-chart/

In the host : 
```
<IP> ether-faucet ether-faucet-api ethereum-lite-explorer geth-bootnode redis-web-interface code-server
```
Backend API Address for Ether-faucet : http://ether-faucet-api


### Uninstall the chart : 

microk8s.helm uninstall ethernetes-chart
