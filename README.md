# Etl Forma
## _Corso cloud_

Esempi di codice di build docker ( docker-images/Dockerfile ) , esempi di deploy stack docker-compose ( compose-samples/sample1/docker-compose.yaml , compose-samples/sample2/docker-compose.yaml ) esempi di deploy applicazioni Kubernetes tramite kubectl ( k8s/deploy ) , esempi di deploy applicazioni su Kubernetes tramite Helm ( k8s/helm )



### Link Utili
### Microsoft Azure
- [ Microsoft Azure Pass , panoramica e come ottenerlo ](https://docs.microsoft.com/it-it/learn/certifications/mocazurepass)
- [ Microsoft Azure Pass ](https://www.microsoftazurepass.com/)
- [Installazione Azure CLI](https://docs.microsoft.com/it-it/cli/azure/install-azure-cli-linux?pivots=apt)
- [Http application routing](https://docs.microsoft.com/it-it/azure/aks/http-application-routing)
- [Https application routing](https://docs.microsoft.com/it-it/azure/aks/ingress-tls)

### Docker
- [Build images](https://docs.docker.com/engine/reference/commandline/image_build/)
- [Run images](https://docs.docker.com/engine/reference/run/)
- [Docker Compose overview](https://docs.docker.com/compose/)

### Kubernetes
 - [Panoramica Kubernetes](https://kubernetes.io/docs/reference/kubectl/overview/)
 - [Getting Started](https://kubernetes.io/docs/setup/)

## Comandi di esempio

#### Login ad Azure da Azure CLI
```
az login
```

#### Login a registro Docker da Azure da Azure CLI
```
az acr login --name nomeregistrocontainerazure
```
#### Visualizzazione zona DNS addon httprouting Kubernetes di Azure da Azure da Azure CLI
```
az aks show --resource-group etl001 --name etl001k8s --query addonProfiles.httpApplicationRouting.config.HTTPApplicationRoutingZoneName -o table
```
 
### Build immagine docker 
```
docker build -t etlformazione001.azurecr.io/etlnginx:1.0
```
 
#### Push immagine docker su registro Azure 
```
docker push etlformazione001.azurecr.io/etlnginx:1.0
```

#### Run immagine docker su registro Azure 
```
docker run -p 80:8080 -d  etlformazione001.azurecr.io/etlnginx:1.0
```

#### Deploy Stack Docker Compose
```
docker-compose -f compose-samples/sample1/docker-compose.yml up -d
```

#### Deploy applicazione su Kubernetes con kubectl
```
kubectl apply -f k8s/deploy/
```

#### Deploy applicazione su Kubernetes con Helm 
```
helm install etl-nginx k8s/helm/
```
