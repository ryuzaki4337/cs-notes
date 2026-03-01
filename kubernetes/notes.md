- Kubernetes
    - Open source container orchestration tool.
    - Developed by Google.
    - Helps you manage containerized applications in different deployment environments(like physical, virutal, cloud etc).

- The need for a container orchestration tool
    - Trend from Monolithe to microservices.
    - Increased usage of containers
    - Demand for a proper way of managing those hundreds of containers.

- Feature of Orchrestration tools offer:
    - High availability or no downtime.
    - Scalability or high performance.
    - Disaster recovery - backup and restore.

- Kubernetes Components
    - Node : A physical or virtual machine that functions as a worker machine in a cluster, providing the compute resources (CPU, memory, storage) to run containerized applications.

    - Pod: 
        - Smallest unit of k8s.
        - Abstraction over container.
        - Usually 1 application per pod.
        - Each Pod gets its own IP address.
        - New IP address on re-creation.

    - Service:
        - Acts as a load balancer as well.
        - Permanent IP address.
        - Lifecycle of Pod and Service not connected.

    - Ingress:
        - Any request initially comes to ingress then it forwards the request to the service.
    
    - ConfigMap:
        - External configuration of your application.
        - Credentials are not meant to be kept in config map.

    - Secret:
        - Used to store secret data.
        - base64 encoded format.
        - The built-in security mechanism is not enabled by default.

    - Volumes:
        - Stoage on local machine or remote(cloud or on-premise).
        - K8s doesn't manage data persistance.

    - Deployment:
        - Blueprint for application pods.
        - Configuration of pods.
        - DB can't be replicated via deployment, because DB has state which is its data.

    - StatefulSet:
        - For stateful apps like databases.
        - it is not easy to maintain hence DBs are often hosted outside of K8s cluster.

- Kubernetes Architecture:
    - Worker machine in K8s cluster:
        - Each node has multiple application pods on it.

        - 3 processes must be installed on every node.
            - Container runtime.
            - Kubelet: It interacts with both the container and node. It starts the pod with a container inside.
            - Kube Proxy : Forwards the requests.
        
        - Worker nodes do the actual work.
    
    - Master processes:
        - 4 processes run on every master node:
            - API Server: 
                - cluster gateway.
                - Acts as a gatekeeper for authentication.
            - Scheduler: 
                - Decides on which node the pod needs to be scheduled based on the resources available on that worker node, where the starting of the pod is actually done by the Kubelet.
            - Controller Manager: 
                - Detects cluster state changes(like pods dying).
                -  In case of pods dying, it makes a call to the scheduler to schedule for new pods.
            - etcd: 
                - Key value store of a cluster store. It is the cluster brain. 
                - Cluster changes get stored in the key value store. 
                - All of the other processes like Scheduler get to know the data available on a worker node based on the data available on 'etcd' etc. 
                - Application data is not stored in etcd

        - K8s cluster is made up of multiple master nodes where each master node run its master processes.

    - Master nodes need less resources where worker nodes need more resources.

    - Add new master/worker node server:
        - Get new bare server.
        - Install all the master / worker node processes.
        - Add it to the cluster.

- kubectl: Command line tool for K8s cluster.