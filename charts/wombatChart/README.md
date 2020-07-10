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
    * Define `hostPath` where WombatOAM is located inside the pod

### Installation:
1. Execute the following command to install WombatOAM: `helm install -f myvalues.yaml wombat stable/wombat`
2. GUI is accessible at `localhost:8080`
3. Log in with the username `admin` and password `admin`

### Uninstallation:
1. To uninstall WombatOAM run the following command: `helm uninstall wombat`

To learn more about the application please visit the [documentations][] webpage.

[documentations]: https://s3.eu-central-1.amazonaws.com/www.wombat-docs.com/getting_started/index.html

## Useful commands
To use these commands it is needed to exec into the pod where WombatOAM is running.

`kubectl exec -it wombat bash --namespace=monitoring`

Navigate to the folder where WombatOAM is located
```
./wombat start  # start WombatOAM
./wombat stop   # stop WombatOAM
```
