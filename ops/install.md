#

This document helps you install kubernetes and asm.

> At present, most of the asm services do not implement identity authentication. If you access the service through the external network, it is recommended to restrict ip access.

# Step 1: Prepare the kubernetes environment
* Hardware recommended configuration

   4-core CPU, 8 GB RAM, 80 GB disk space

* Install kubernetes

   It is recommended that you use [kubekey project](https://github.com/kubesphere/kubekey/) to install kubernetes

   ```
   ./kk create cluster --with-kubernetes v1.24.1
   ```

* Install kubesphere (optional)

   Kubesphere can be used to manage k8s clusters and provides `ingress controller`.

   You can install the `v3.3.1` version with the following command. Before installation, you need to have a default StorageClass. Why and how to create a default StorageClass can be found in [this issue](https://github.com/leveryd-asm/asm/issues/38)
   ```
   kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.3.1/kubesphere-installer.yaml
   kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.3.1/cluster-configuration.yaml
   ```

   > For detailed installation steps, refer to [kubesphere](https://kubesphere.io/docs/v3.3/quick-start/minimal-kubesphere-on-k8s/), you can also use [kubekey project](https://github.com/kubesphere/kubekey/) to quickly install kubernetes and kubesphere.

   If you don't need kubesphere, you can use `ingress-nginx` as `ingress controller`.

# Step 2: Download the project code to the local

Download and switch to the project root directory
```
git clone https://github.com/leveryd-asm/asm --depth 1
cd asm/
```

# Step 3: Start the installation project

When installing for the first time, you need to execute `helm dependency update` to download dependencies.

Executing the following command will create the asm namespace and install the project in the asm namespace
```
kubectl create namespace asm
helm -n asm template ./ | kubectl apply -n asm -f -
```

You can also pass parameters to helm to modify the installation configuration, for example, the following command will use `asm-manage.com` as the domain name to access the console
```
helm -n asm template ./ --set console_domain=asm-manage.com | kubectl apply -n asm -f -
```

# Step 4: Verify that the installation was successful

Check whether the pod status is running
```
kubectl get pod -n asm
```

# Step 5: Verify that the asm console is accessible

After the asm instance is installed, you can enter the asm console through the browser to manage assets, management tasks, and operation alarms

* Create gateway (ingress)

   If you have kubesphere installed, you can create a gateway on the kubesphere console

   ![](https://user-images.githubusercontent.com/1846319/226091298-d13f5e7e-6d61-4648-bcb3-fdec2da96e92.png)

* Find the nodeport of the ingress

   If you have installed kubesphere, you can execute the following command, the command result shows that `node ip:32115` can be accessed outside the cluster
   ```
   [root@192 ~]# kubectl get pod -n kubesphere-controls-system | grep -i kubesphere-router-kubesphere-system
   kubesphere-router-kubesphere-system-5cfc84c77c-jh42b 1/1 Running 15 24d
   [root@192 ~]# kubectl get service -A | grep kubesphere-router-kubesphere-system
   kubesphere-controls-system kubesphere-router-kubesphere-system NodePort 10.233.44.102 <none> 80:32115/TCP,443:31474/TCP 95d
   ```

   Or find the `console` ingress access address on the `kubesphere` console, as shown in the figure below

   ![](https://user-images.githubusercontent.com/1846319/209645921-d845c719-4f31-4e88-ae7c-c4326019b90a.png)

   ![](https://user-images.githubusercontent.com/1846319/209645971-34b5443c-bcd3-46a2-84a8-fa2378cbc9df.png)


* Bind domain name to node ip

   The console domain name is `console.com` by default

   The host file path under mac is in `/etc/hosts`, and the host file path under windows is in `C:\Windows\System32\drivers\etc\hosts`

   > You can also use [SwitchHosts](https://github.com/oldj/SwitchHosts) to manage hosts file

* Access the asm console on the browser

   ![](https://user-images.githubusercontent.com/1846319/225215933-1a8bec34-c07e-4ce2-8d88-ee805e72796a.png)
