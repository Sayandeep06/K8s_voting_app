Kubernetes Voting App
=====================

This project demonstrates the setup and deployment of a simple voting app on Kubernetes. The app consists of several components, each running in its own Kubernetes pod. The components include a voting app written in Python, a Redis database, a worker service, a PostgreSQL database, and a result app written in JavaScript.![Screenshot from 2023-11-13 17-45-40](https://github.com/Sayandeep06/K8s_voting_app/assets/100061797/f48f1c05-34d4-4f3c-8029-a14209ba3ab5)


Prerequisites
-------------

-   [Docker](https://www.docker.com/) installed
-   [Minikube](https://minikube.sigs.k8s.io/) installed
-   [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) installed

Setup
-----

1.  Clone this repository:

    
    ```
    git clone https://github.com/Sayandeep06/K8s_voting_app
    cd kubernetes-voting-app
    ```

2.  Create Kubernetes pod configurations:

    -   Create `voting-app-pod.yaml` for the Python voting app.
    -   Create `redispod.yaml` for the Redis pod.
    -   Create `worker-pod.yaml` for the worker service.
    -   Create `postgres-pod.yaml` for the PostgreSQL pod.
    -   Create `result-app-pod.yaml` for the JavaScript result app.
3.  Create Kubernetes service configurations:

    -   Create `redis-service.yaml` for the Redis ClusterIP service.
    -   Create `postgres-service.yaml` for the PostgreSQL ClusterIP service.
    -   Create `voting-app-service.yaml` for the NodePort service of the voting app.
    -   Create `result-app-service.yaml` for the NodePort service of the result app.

Deploying on Kubernetes
-----------------------

1.  Start Minikube:

    ```

    minikube start
    ```

2.  Deploy the app components:

    ```
    kubectl create -f voting-app-pod.yaml
    kubectl create -f redispod.yaml
    kubectl create -f worker-pod.yaml
    kubectl create -f postgres-pod.yaml
    kubectl create -f result-app-pod.yaml
    ```

3.  Create services:
    ```
    kubectl create -f redis-service.yaml
    kubectl create -f postgres-service.yaml
    kubectl create -f voting-app-service.yaml
    kubectl create -f result-app-service.yaml
    ```

4.  Check pods and services:

    ```

    kubectl get pods
    kubectl get services
    ```

5.  Get URLs for services:

    ```

    minikube service voting-app-service --url
    minikube service result-app-service --url
    ```
    ![Screenshot from 2023-11-13 16-41-09](https://github.com/Sayandeep06/K8s_voting_app/assets/100061797/7f1518ed-26d4-424d-88b3-7cbc007d3650)


Deploying with Deployments
--------------------------

1.  Create deployment configurations:

    -   Create `voting-app-deployment.yaml` for the voting app deployment.
    -   Create `redis-deployment.yaml` for the Redis deployment.
    -   Create `worker-deployment.yaml` for the worker deployment.
    -   Create `postgres-deployment.yaml` for the PostgreSQL deployment.
    -   Create `result-app-deployment.yaml` for the result app deployment.
2.  Create services (same as before).

3.  Deploy deployments and services:

    ```

    kubectl create -f voting-app-deployment.yaml
    kubectl create -f redis-deployment.yaml
    kubectl create -f worker-deployment.yaml
    kubectl create -f postgres-deployment.yaml
    kubectl create -f result-app-deployment.yaml

    kubectl create -f redis-service.yaml
    kubectl create -f postgres-service.yaml
    kubectl create -f voting-app-service.yaml
    kubectl create -f result-app-service.yaml
    ```

4.  Get URLs for services:

  
    ```
    minikube service voting-app-service --url
    minikube service result-app-service --url
    ```
    ![Screenshot from 2023-11-13 15-52-48](https://github.com/Sayandeep06/K8s_voting_app/assets/100061797/c7f6891c-01f3-4632-8426-bf885367449c)


Scaling Deployments
-------------------

To scale the voting app deployment:

```

kubectl scale deployment voting-app-deploy --replicas=3
```

Adjust the number of replicas as needed.

This concludes the setup and deployment of the Kubernetes voting app. Adjust configurations and scale deployments based on your requirements.
