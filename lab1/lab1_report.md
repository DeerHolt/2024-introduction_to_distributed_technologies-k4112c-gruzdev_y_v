```
University: [ITMO University](https://itmo.ru/ru/) 
Faculty: [FICT](https://fict.itmo.ru) 
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies) \
Year: 2024
Group: K4112c
Author: Gruzdev Yaroslav
Lab: Lab1
Date of create: 12.12.2024
Date of finished: 12.12.2024
```

### 1. Run minikube
    $ minikube start

### 2. Написание манифест файла для развертывания vault
Директория содержит в себе файл `vault.yaml`, в котором описана конфигурация развертывания пода vault и сервиса vault-service.  
Pod содержит информацию об использованном образе и порте сервиса vault и создает pod с нашим сервисом.  
Service управляет доступом к pod'у и позволяет перенаправлять на него запросы.

``` yaml
apiVersion: v1
kind: Pod                                            
metadata:
  name: vault
  labels:
    app: vault                         
spec:                                                
  containers:
    - image: vault:latest
      name: vault                             
      ports:
      - name: vault-port
        containerPort: 8200
```
## Contents
- manifest/vault-pod.yaml: manifest for deploying vault pod
- answers.txt: FAQ
- diagram.png: diagram of this kubernetes setup
- images/image1.png, image2.png, image3.png, image4.png: screenshots of the work

## Commands used:
- minikube start
- kubectl apply -f vault-pod.yaml
- minikube kubectl -- expose pod vault --type=NodePort --port=8200
- minikube kubectl -- port-forward service/vault 8200:8200
- kubectl logs vault
