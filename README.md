# Introduction
This chart is an **unofficial** install of [Peertube](https://github.com/Chocobozzz/PeerTube), made to work in kubernetes **>=1.23** with helm 3.
The Peertube version is **5.0.1**. A minimal amount of **manual configuration** is still required in order to make this chart work.
You can either use a handmade values.yaml to use upon install **OR** clone the repository and edit the values.yaml in the helm directory. The second one is preferred.

## Install
First go to helm/values.yaml and tweak it to your specific configuration.
When the configuration of the helm/values.yaml is finished, you must install the helm chart running this command :

*make sure you have helm installed allready, if not refer to the [official install](https://helm.sh/docs/intro/install/)*

```
helm dependency build /path/to/chart
helm install --create-namespace -n yourNameSpace yourReleaseName /path/to/chart
```

## Uninstall
to uninstall the chart run the following commands :

**WARNING ! all volumes will be deleted and all data will be lost !**


``` 
helm delete -n yourNameSpace yourReleaseName 
kubectl delete namespaces yourNameSpace
```

## Notes
For now (2023-03-08) this chart only support transcoding by cpu. Gpu transcoding is available via custom profiles, which I am unfamiliar with.
(2023-03-09) Firefox and Chromium have been tested and both works.
