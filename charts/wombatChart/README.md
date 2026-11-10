# WombatOAM

WombatOAM (or Wombat for short) is an **operations and maintenance tool** for
**Erlang systems**.

## Wombat Installation

The docker image contains the all the necessary prerequisites (Erlang) to run WombatOAM.

### Prerequisites:
1. A WombatOAM license that permits Kubernetes. Without it WombatOAM refuses
   to run in the cluster and to manage nodes running in pods.
2. Define a `values.yaml` file for the necessary environment variables
     * Define the following parameters under `kubernetesDiscovery` in order to automatically
     add the pods of a service to WombatOAM
        * namespace
        * service
        * appname
        * cookie
        * nodeExpiryHours (optional): hours a node may be missing from the service
          DNS before WombatOAM removes it (default 120)

       Values set here are read-only in the WombatOAM GUI. Leave any of them
       empty to set it in the GUI instead, under Configuration > Kubernetes
       (WombatOAM 4.3.0 and later).
    * Define `hostPath`: a directory on the Kubernetes node for WombatOAM's
      data and logs. Put the license there as `license.lic_key`.
    * Set `wombatConfig.enabled: true` (optional, recommended when settings are
      managed from the GUI) to keep `wombat.config` in `<hostPath>/config`, so
      that settings saved from the GUI survive the pod being recreated.

### Installation:
1. Execute the following command to install WombatOAM: `helm install -f myvalues.yaml wombat wombat/wombat`
2. GUI is accessible at `localhost:8080`
3. Log in with the username `admin` and password `admin`

### Uninstallation:
1. To uninstall WombatOAM run the following command: `helm uninstall wombat`

To learn more about the application please visit the [Documentation page][].

[Documentation page]: https://wombat-docs.fly.dev/kubernetes.html

## Useful commands
To use these commands it is needed to exec into the pod where WombatOAM is running.

`kubectl exec -it wombat bash --namespace=monitoring`

Navigate to the folder where WombatOAM is located
```
./wombat start  # start WombatOAM
./wombat stop   # stop WombatOAM
```
