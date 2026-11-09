# WombatOAM

WombatOAM (or Wombat for short) is an **operations and maintenance tool** for
**Erlang systems**.

## Wombat Installation

The docker image contains the all the necessary prerequisites (Erlang) to run WombatOAM.

### Prerequisites:
1. Define a `values.yaml` file for the necessary environment variables
     * Define the following parameters under `kubernetesDiscovery` in order to automatically 
     add them to WombatOAM
        * namespace
        * service
        * appname
        * cookie
        * nodeExpiryHours (optional): hours a node may be missing from the service
          DNS before WombatOAM removes it (default 120)
    * Define `hostPath` where WombatOAM is located inside the pod
    * Set `wombatConfig.enabled: true` (optional) to keep `wombat.config` in
      `<hostPath>/config`, so that settings saved from the GUI survive the pod
      being recreated. Discovery settings set under `kubernetesDiscovery` are
      read-only in the GUI: leave one empty to manage it from the GUI instead.

### Installation:
1. Execute the following command to install WombatOAM: `helm install -f myvalues.yaml wombat stable/wombat`
2. GUI is accessible at `localhost:8080`
3. Log in with the username `admin` and password `admin`

### Uninstallation:
1. To uninstall WombatOAM run the following command: `helm uninstall wombat`

To learn more about the application please visit the [Documentation page][].

[Documentation page]: https://wombat-docs.fly.dev/

## Useful commands
To use these commands it is needed to exec into the pod where WombatOAM is running.

`kubectl exec -it wombat bash --namespace=monitoring`

Navigate to the folder where WombatOAM is located
```
./wombat start  # start WombatOAM
./wombat stop   # stop WombatOAM
```
