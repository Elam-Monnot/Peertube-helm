# Introduction
This chart is an **unofficial** install of [Peertube](https://github.com/Chocobozzz/PeerTube), made to work in kubernetes **>=1.23** with **Helm >=3.11.1**.  
The Peertube version is **5.0.1**. A minimal amount of **manual configuration** is still required in order to make this chart work.  
You can either use a handmade values.yaml to use upon install **OR** clone the repository and edit the values.yaml in the helm directory.  
**The second one is preferred.**

## Install
First go to helm/values.yaml and tweak it to your specific configuration.
When the configuration of the helm/values.yaml is finished, you must install the helm chart running this command :

:bulb:*Make sure you have helm installed allready, if not refer to the [official install](https://helm.sh/docs/intro/install/)*

```
helm repo add mail https://bokysan.github.io/docker-postfix
helm repo add postgresql https://charts.bitnami.com/bitnami
helm repo add redis https://charts.bitnami.com/bitnami
helm dependency build /path/to/chart
helm install --create-namespace -n yourNameSpace yourReleaseName /path/to/chart
```

The chart comes bundled with dedicated redis, postgresql and smtp servers.
## Uninstall
to uninstall the chart run the following commands :

:warning: **All volumes will be deleted and all data will be lost !**   
*If installed in the default namespace, you won't be able to delete the namespace, delete each ressources instead.*

``` 
helm delete -n yourNameSpace yourReleaseName 
kubectl delete namespaces yourNameSpace
```
## Notes :memo:
 - For now (2023-03-08) this chart only support transcoding by cpu. Gpu transcoding is available via custom profiles, which I am unfamiliar with.
 - (2023-03-09) Firefox and Chromium have been tested and both works.  
 - Special thanks to [LecyneNoir](https://git.lecygnenoir.info/LecygneNoir), this chart is based on his work, I updated it for a newer version of PeerTube and added some tweaks.
