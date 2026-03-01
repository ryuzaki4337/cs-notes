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
        - Abstraction over Pods.
        - Configuration of pods.
        - DB can't be replicated via deployment, because DB has state which is its data.
        - Deployment manages ReplicaSets
        - Supports rolling updates and rollbacks
        - Maintains desired number of replicas

    - StatefulSet:
        - For stateful apps like databases.
        - it is not easy to maintain hence DBs are often hosted outside of K8s cluster.
        - Stable network identity (pod-0, pod-1)
        - Stable persistent storage
        - Ordered pod startup/shutdown
        - Pods are not interchangeable

    - Replicaset:
        - Ensures a specified number of identical Pods are running
        - Uses label selectors
        - Usually not created directly — managed by Deployment
        - No rolling update / rollback management, hence not used directly.

    - DaemonSet:
        - ensures One pod runs on every node (or selected nodes)
        - Common uses:
            - Log collectors (Fluentd)
            - Monitoring agents (Prometheus node exporter)
            - Security agents
            - CNI plugins
        - Why can’t Deployment do this? Because Deployment schedules based on replica count — not one-per-node.

- Kubernetes Architecture:
    - Worker machine in K8s cluster:
        - Each node has multiple application pods on it.

        - 3 processes must be installed on every node.
            - Kubelet: It interacts with both the container and node. It starts the pod with a container inside. communicates with API server and manages pods
            - Kube Proxy : handles networking and service routing.
            - Container runtime: runs containers
        
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
                - Controller Manager continuously compares:
                    - Desired state (from etcd via API Server)
                    - Actual state
                - If a pod dies:
                    - Controller updates the desired state (creates a new Pod object)
                    - Scheduler detects an unscheduled pod and assigns it to a node
                    - Kubelet on that node actually creates the pod
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

- kubectl commands: [Link](https://gitlab.com/nanuchi/youtube-tutorial-series/-/blob/master/basic-kubectl-commands/cli-commands.md)

- K8s Yaml Configuration File:
    - Metadata: Name, label etc.
    - Specification: Configuration of the specific component mentioned in the type
    - Status: 
        - Automatically generated and added by K8s. 
        - In case of any misalignment with the current state and specification, then K8s will automatically adjust the cluster state to match the specification. 
        - For example, if the number of replicas in the current state is 1, but the number of replicas mentioned in the specification is 2, then K8s automatically adds a new replica. 
        - K8s gets the status from the etcd.

    - YAML has a strict indentation policy.

    - type: LoadBalancer in service assigns service an external IP address and so accepts external requests.

    - nodePort while exposing a service as external service must be between 30000 - 32767

    - type ClusterIP in service has only internal IP address, but LoadBalancer has both internal and external IP addresses.

- NameSpace:
    - Organize resources in namespaces
    - Virtual cluster inside a cluster
    - 4 four of namespaces.
    - kubernetes-dashboard only with minikube
    - kube-system: Do not create or modify in kube-system.
    - kube-public: 
        - Publicely accessible data
        - A configMap, which contains cluster information.
    - kube-node-lease:
        - Heartbeats of nodes
        - Each node has associated lease object in namespace.
        - Determines the availability of a node.
    - default: 
        - Resources you create are located here.
    - Use Cases when to use Namespaces:
        - Structure your components.
        - Avoid conflicts between teams.
        - Share services between different environments.
        - Limit resources like CPU, RAM, storage per namespace.

    - Each namespace should create their own configMap / secret.
    - Service can be accessed in another namespace.
    - Volumes can't be created within a namespace. They live globally in a cluster. They can't be isolate them.
    - By default, components are created in the default namespace.

- Ingress Controller:
    - Evaluates all the rules defined in the ingress.
    - Manages redirections
    - Entrypoint to cluster
    - Many third-party implementations.
    - K8s Nginx ingress controller.

- Helm:
    - Package manager for Kubernetes.
    - To package YAML files and distribute them in public and private repositories.

- Helm Charts
    - Bundle of YAML files.
    - Create your own helm charts with helm.
    - Push them to helm repository.
    - Download and use existing ones.

- Volumes:
    - Persistent Volume
        - A cluster resource that is used to store data.
        - Created via YAML file
            - kind: PersistentVolume
            - spec: ex, how much storage?
        - Needs actual physical storage, like local disk, cloud storage.
        - They are outside of the namespaces; accesible to the whole cluster. 

    - Persistent Volume Claim
    - Storage Class

    - Storage Requirements:
        - Storage that doesn't depend on the pod lifecycle.
        - Storage must be available on all nodes.
        - Storage needs to survive even if cluster crashes.

- Stateful Set:
    - Examples of stateful applications: databases, applications that stores data.
    - Stateless application:
        - Don't keep record of state
        - Each request is completely new.
        - Deployed using deployment.

    - Stateful applications are deployed using stateful set.

    - Configure storage the same way.

- Deployment vs StatefulSet:
    - Replicating stateful applications is more difficult.
    - Stateful set pods:
        - Can't be created/deleted at same time.
        - Can't be randomly addressed.
        - Replica pods are not identical - Pod identity.

    - Stateful applications are not perfect for containerized enviroments.

- Services:
    - Each Pods has its own IP address.
    - Pods are ephemeral - are destroyed frequently.
    - Service gives stable IP address.
    - It also provides load balancing.
    - Loose coupling.
    - Within & outside cluster.

- ClusterIP services:
    - Exposes service internally within the cluster.
    - Default type.
    - Gets a virtual IP
    - Traffic flow: Pod → ClusterIP → kube-proxy → Target Pod
    - Cannot be accessed from outside cluster

- Headless services:
    - Clients wants to communicate with 1 specific pod directly.
    - Pods want to talk directly with specific pod.
    - So, not randomly selected.
    - Use Case: Stateful applications like databases.
    - Traffic flow: Client → Pod IP directly
    - No virtual IP is created
    - No kube-proxy load balancing needed

    - Client needs to figure out IP addresses of each pod.

    - Option 1: API call to K8s API service to fetch the pod details.
        - Makes app too tied to K8s API.
        - inefficient.
    
    - Option 2: DNS lookup
        - DNS lookup for Service - return single IP address (ClusterIP)
        - Set ClusterIP to "None" - returns Pod IP address instead

- NodePort Services:
    - External traffic has access to fixed port on each worker node.
    - Range: 30000 - 32767
    - It is not secure, not for external connection.
    - Traffic flow: Client → NodeIP:NodePort → kube-proxy → Pod

- LoadBalancer Services:
    - Is an extension of NodePort service, which in turn is an extension of ClusterIP.
    - Used in cloud environments.
    - Provisions external cloud load balancer
    - NodePort and ClusterIP service are created automatically.
    - Range: 30000 - 32767
    - Traffic flow: External Client → Cloud Load Balancer → NodePort → kube-proxy → Pod

- Configure Ingress and LoadBalancer for production environments.

- When kubectl apply -f deployment.yaml
    - Step 1: kubectl Talks to API Server
        - kubectl reads the YAML
        - Converts it into JSON
        - Sends a REST API request to the kube-apiserver

    - Step 2 — Authentication & Authorization
        - API server:
            - Authenticates the user (certificate / token / RBAC)
            - Checks authorization (RBAC rules)
            - If allowed → proceeds

    - Step 3 — Admission Controllers
        - Before storing the object:
        - Mutating admission controllers may modify the object
        - Validating admission controllers may reject it

        - Example:
            - Resource quotas
            - Pod security policies
            - Defaulting values

    - Step 4 — Object Stored in etcd
        - If everything passes:
            - API server stores the desired state in etcd
            - Now Kubernetes knows:
                - "User wants a Deployment with 3 replicas"

    - Step 5 — Controller Manager Reacts
        - Deployment controller:
            - Sees new Deployment
            - Creates a ReplicaSet

        - ReplicaSet controller:
            - Sees desired replicas (say 3)
            - Creates 3 Pod objects (unscheduled)

    - Step 6 — Scheduler Assigns Nodes
        - Scheduler:
            - Watches for Pods without a node
            - Evaluates nodes based on:
                - CPU/memory
                - Taints/tolerations
                - Node selectors

            - Assigns a node to each pod

    - Step 7 — Kubelet Creates Containers
        - On the selected worker node:
            - kubelet notices the Pod assigned to it
            - Pulls the image
            - Talks to container runtime (containerd)
            - Starts containers

    - Step 8 — kube-proxy Updates Networking
        - kube-proxy updates iptables/ipvs
        - Ensures service routing works

- Services will NOT work properly without kube-proxy. Headless Services can still work without kube-proxy. Because they bypass virtual IP routing.

- Pending means the pod has not been scheduled onto a node yet.
    - Common Reasons for Pending:
        - Insufficient Resources
        - Taints & Tolerations: 
            - If node has:
                taints:
                    key=value:NoSchedule
            - And pod has no matching toleration → stays Pending.

        - Node Selector / Affinity Issues
            - If pod has:
                nodeSelector:
                    disktype: ssd
            - But no node has that label → Pending forever.
        - Resource Quotas: Namespace quota exceeded.

- CrashLoopBackOff → container issue; Pending → scheduling issue

- Even if kubectl top nodes shows free memory, Kubernetes scheduler uses resource requests, not actual usage. If existing pods have high memory requests, the scheduler may not find enough allocatable memory for the new pod, resulting in an Insufficient memory error.

- If no requests are defined and scheduling still fails, I would check for a LimitRange in the namespace. LimitRange can automatically assign default resource requests, which may cause the scheduler to reject the pod due to insufficient allocatable memory.

- HPA scales based on:
    - CPU utilization (most common)
    - Memory utilization
    - Custom metrics (Prometheus)
    - External metrics (queue length, requests/sec)

    Also:
    - HPA works by modifying: .spec.replicas of a Deployment/ReplicaSet/StatefulSet.
    - Important: HPA does NOT directly create pods.

    - HPA is preferred for stateless workloads because horizontal scaling is safer and avoids restarts.

- VPA cannot resize a running pod.
    - Recommends new CPU/memory values
    - Evicts the pod
    - Recreates it with new resource requests
    - So there is a restart involved.

- Cluster Autoscaler scales nodes, not pods.
    - Adds new nodes when pods cannot be scheduled
    - Removes nodes when underutilized

- HPA scales the number of pods based on resource or custom metrics. VPA adjusts resource requests of individual pods by recreating them with updated values. Cluster Autoscaler scales the number of nodes in the cluster when there are unschedulable pods or removes underutilized nodes. Together, HPA handles pod-level scaling and Cluster Autoscaler handles infrastructure-level scaling.

- If scaling to 20 pods doesn’t improve latency and CPU is only 40%, I would suspect the bottleneck is not CPU-bound. It could be an application-level concurrency limitation, a downstream dependency like a database bottleneck, or the wrong scaling metric being used. In such cases, scaling horizontally won’t solve the issue unless the true bottleneck is identified.

- When a node crashes, its heartbeats stop and the control plane marks it NotReady. After a grace period, the Node Controller evicts the pods. Replica-based controllers detect the missing replicas and create new Pod objects. The scheduler assigns them to healthy nodes. Services automatically remove the failed pod endpoints. If there isn’t enough capacity, Cluster Autoscaler may add new nodes.

- If the node comes back before the pod eviction timeout, it will be marked Ready again and the existing pods will continue running. If it comes back after eviction, the controllers would have already recreated the pods elsewhere, and the kubelet will terminate any orphaned containers when the node rejoins.

- By default:
    - Node heartbeat grace period ≈ 40 seconds
    - Pod eviction timeout ≈ 5 minutes