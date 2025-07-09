
## [Kubernetes Learning](https://drive.google.com/drive/folders/1Yvs-iRxr2cFnVcL3eOHwiLiLrlD0HIok)

### 🚀 **Kubernetes Overview (K8s)**

1. **Open Source**:
   Kubernetes is an **open-source platform** developed for automating the **deployment, management, and scaling** of **containerized applications**.

2. **Use Case**:
   It is especially useful **when you're working with containers**, particularly in **production environments**, where managing multiple containers manually becomes complex.

3. **Benefits**:

   * Handles **automatic deployment**.
   * Manages the **lifecycle of containerized applications**.
   * Helps in **scaling applications** based on traffic/load.

4. **Infrastructure Support**:
   Kubernetes supports **different types of infrastructures**:

   * **Virtual Machines (VMs)**
   * **Cloud Infrastructure** (AWS, GCP, Azure, etc.)

5. **Why Use Kubernetes?**

   * Ideal for applications running in **containerized form**.
   * Supports high **availability**, **load balancing**, **auto-scaling**, and **self-healing** (restarting failed containers automatically).

---

### 🎼 **Understanding Kubernetes with Orchestration Analogy**

#### 1. **What is Orchestration?**

* Think of an **orchestra**:
  It has many **musicians** playing different instruments. Despite their skill, someone needs to **coordinate** them to produce **harmonious music**.

* In this analogy:

  * The **musicians** = **containers**
  * The **orchestra master/conductor** = **Kubernetes**
  * The **music sheet/book of rules** = **Kubernetes configuration (YAML)**

---

### 📦 **Kubernetes as a Container Orchestrator**

#### 2. **Kubernetes Role**

* Kubernetes **acts as the master/controller** that manages and coordinates all containers running across infrastructure (servers, VMs, or cloud).
* Just like a conductor ensures every musician is in sync, Kubernetes ensures all containers:

  * Are deployed correctly
  * Communicate with each other
  * Recover automatically if something fails
  * Scale up/down based on load

---

### ⚙️ **What Does Kubernetes Manage?**

* **Containerized Applications**: Applications packed in containers and running on an infrastructure.
* **Container States**: Keeps track of the health, status, and lifecycle of each container.
* **Infrastructure**: Works across physical servers, virtual machines, or cloud environments.

---

### 📘 **Configuration Files (YAML)**

* Kubernetes uses **configuration files** (mostly written in **YAML format**) to define:

  * Deployment rules
  * Desired state of containers
  * Scaling policies
  * Health checks
* These files are like the **instruction manual** or **music book** telling Kubernetes how things should be managed.

---

### 💡 **Key Takeaways**

| Concept              | Description                                                                      |
| -------------------- | -------------------------------------------------------------------------------- |
| **Orchestration**    | Managing multiple containers automatically, just like coordinating an orchestra. |
| **Kubernetes (K8s)** | Acts as a **master/controller** to manage, deploy, and scale containerized apps. |
| **Containers**       | Independent units (like musicians) running parts of the application.             |
| **Configuration**    | YAML files define the rules, states, and setup for Kubernetes to follow.         |
| **Infrastructure**   | Can run on VMs, physical servers, or cloud platforms.                            |
| **Goal**             | Ensure **reliable, automated, and scalable** container management.               |

---

Here is a **detailed English summary** of the **real-life Kubernetes use case** and key concepts explained in your transcript:

---

### 🌐 **Real-Life Use Case of Kubernetes**

#### 🧑‍💻 Scenario: A Developer Builds a Web App

1. A developer **builds a website/web app**.
2. Packages the app into **Docker containers**.
3. Deploys it to a **single server**.

At this point:

* The application runs fine.
* Users can access it without issues.

---

### ⚠️ **Problems with Single-Server Deployment**

#### 🔸 **Problem 1: High Traffic / Load**

* If the app becomes **popular**, traffic increases.
* A **single server may not handle** the heavy load.
* The result:

  * App might **crash** or become **very slow**.

#### 🔸 **Problem 2: Server Failure**

* If the **server crashes**, the **entire application goes down**.
* This causes:

  * **Downtime**
  * **User dissatisfaction**
  * **Manual effort to detect and fix** the issue

---

### ✅ **Solution: Multi-Server / Clustered Deployment**

To handle these issues, the developer:

* **Removes dependency on a single server**
* **Deploys the app on multiple servers (nodes)**

#### 🔹 **Benefits of This Approach**:

| Benefit               | Description                                                                 |
| --------------------- | --------------------------------------------------------------------------- |
| **High Availability** | If one server goes down, others are still running — **no downtime**         |
| **Load Balancing**    | Traffic gets **distributed across multiple servers** for better performance |
| **Redundancy**        | Multiple instances of the app ensure **failover capability**                |

---

### 🧠 **Why Kubernetes is Needed**

Now even with multiple servers:

* Manually managing:

  * Deployment
  * Health checks
  * Monitoring
  * Scaling
    across **multiple containers and servers** becomes **very difficult and error-prone**.

That’s where **Kubernetes** comes in:

#### 📌 **Kubernetes Helps With**:

* **Orchestrating** all containers across multiple servers
* **Automating deployments**
* **Monitoring and health checks**
* **Self-healing** (e.g., restarting failed containers)
* **Scaling up/down automatically**
* **Load balancing**
* **Zero downtime rollouts and updates**

---

### 📋 Summary of Key Points

| Concept                       | Explanation                                                |
| ----------------------------- | ---------------------------------------------------------- |
| **Docker**                    | Tool used to containerize the web app                      |
| **Single Server Problem**     | Risk of crash under load or failure, leading to downtime   |
| **Multi-Server Solution**     | Improves availability and load handling                    |
| **Kubernetes**                | Automates management of containers across multiple servers |
| **Scaling**                   | Handles traffic spikes by scaling containers dynamically   |
| **Monitoring & Self-Healing** | Detects failed containers and restarts them automatically  |

---

## 🏗️ Kubernetes Architecture — Explained with Key Components

### 🧩 1. **What Happens When You Deploy Kubernetes?**

* When you install Kubernetes in your environment/infrastructure, you set up a **Kubernetes Cluster**.
* A **cluster** has two main parts:

  1. **Control Plane (Master Node)**
  2. **Worker Nodes**

---

## ⚙️ 2. **Key Components of Kubernetes Architecture**

### 🧠 **A. Control Plane (Master Node)**

* Acts as the **“Orchestrator”** — like the conductor in a music band.
* Manages the overall cluster.
* Makes **global decisions**, like scheduling, monitoring, and maintaining desired state.
* Key components in the Control Plane:

| Component              | Description                                                                              |
| ---------------------- | ---------------------------------------------------------------------------------------- |
| **API Server**         | Entry point to the Kubernetes cluster. Accepts REST requests (e.g., `kubectl` commands). |
| **Scheduler**          | Assigns containers (pods) to worker nodes.                                               |
| **Controller Manager** | Watches cluster state and attempts to maintain the desired state.                        |
| **etcd**               | Distributed key-value store for cluster configuration and state data.                    |

---

### ⚙️ **B. Worker Nodes (Minions)**

* These are the **servers** (physical/virtual/cloud) where actual application containers run.
* Each node is part of the cluster and runs key components:

| Component             | Description                                                                              |
| --------------------- | ---------------------------------------------------------------------------------------- |
| **kubelet**           | Agent on the node that communicates with the control plane, manages pods and containers. |
| **Container Runtime** | The engine (e.g., Docker, containerd) that actually runs containers.                     |
| **kube-proxy**        | Maintains network rules for pod communication inside/outside the cluster.                |

---

## 📦 3. **Node vs Cluster**

* **Node**: A single server (VM, bare-metal, or cloud instance) running one or more containers.
* **Cluster**: A **group of nodes** managed together, forming a single logical system.

---

## 📡 4. **Communication & Management**

* The **API Server** connects with **kubelets** on each worker node to manage container lifecycles.
* The control plane constantly monitors the health of nodes and pods.

---

## 🔁 5. **Optional: Master on Worker Node**

* Ideally, the **Master node** should be on a **separate server** for high availability.
* But **it can be co-located** on a worker node in smaller or test environments.

---

## 🖼️ Kubernetes Architecture Diagram

Below is a simple Kubernetes architecture diagram to visualize how everything works together:

```
                          +-----------------------+
                          |    Control Plane      |
                          |  (Master Node)        |
                          |                       |
                          |  - API Server         |
                          |  - Scheduler          |
                          |  - Controller Manager |
                          |  - etcd               |
                          +----------+------------+
                                     |
           ----------------------------------------------------
           |                        |                          |
+----------------+     +----------------+         +----------------+
|   Worker Node 1 |     |  Worker Node 2 |         | Worker Node 3  |
|----------------|     |----------------|         |----------------|
| - kubelet      |     | - kubelet      |         | - kubelet      |
| - kube-proxy   |     | - kube-proxy   |         | - kube-proxy   |
| - Containers   |     | - Containers   |         | - Containers   |
+----------------+     +----------------+         +----------------+

```

---

## 📝 Summary Table of Key Concepts

| Term                   | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| **Kubernetes Cluster** | Group of machines (nodes) managed together.                  |
| **Control Plane**      | The brain of Kubernetes — makes decisions and manages nodes. |
| **Worker Node**        | Actual servers that run containers (your app).               |
| **kubelet**            | Agent that connects worker node with control plane.          |
| **API Server**         | Gateway for communication into the Kubernetes system.        |
| **kube-proxy**         | Manages network routing on each node.                        |
| **etcd**               | Distributed key-value store for configuration/state data.    |

---

## 🧩 Kubernetes Components

Kubernetes is composed of multiple components working together across the **Control Plane (Master)** and **Worker Nodes**.

---

### ⚙️ **I. Control Plane Components (Master Node)**

| Component              | Description                                                                                                                                         |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **API Server**         | Acts as the **main entry point** for the cluster. It handles **RESTful requests** and **communicates with kubelets**. It's what `kubectl` talks to. |
| **Scheduler**          | Decides **which node** will run a newly created Pod based on resource availability.                                                                 |
| **etcd**               | A **key-value store** that stores **cluster state and configuration** data.                                                                         |
| **Controller Manager** | Manages the **desired state** of the cluster. If a Pod fails or is unresponsive, it ensures corrective action (e.g., rescheduling it).              |

🧠 **Use Analogy**:
Think of Control Plane as the **brain or conductor** in an orchestra that ensures everything runs in sync.

---

### ⚙️ **II. Node Components (Worker Nodes)**

| Component             | Description                                                                                                                             |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **kubelet**           | An **agent on each worker node** that receives instructions from the API server and **ensures the containers in the Pods are running**. |
| **kube-proxy**        | Manages **network routing rules**. Ensures that traffic is **routed properly within the cluster and outside it**.                       |
| **Container Runtime** | Tool responsible for **running the actual containers**. Common runtimes: Docker, containerd, CRI-O.                                     |

---

### 📦 **III. Pods & Containers**

| Concept       | Description                                                                                                                                        |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pod**       | The **smallest deployable unit** in Kubernetes. A Pod can run **one or more containers** in a shared, isolated environment (same network/storage). |
| **Container** | An application’s instance running inside a Pod, managed by a runtime like Docker.                                                                  |

🔹 **Note**:

* Pods **encapsulate** containers.
* Multiple containers in a Pod can **share resources** and **communicate** with each other.

---

## 🧠 How These Work Together:

1. You define desired state (e.g., run 3 replicas of a web app).
2. The **API Server** receives it.
3. The **Scheduler** picks suitable nodes.
4. The **Controller Manager** ensures Pods are healthy and match the desired state.
5. On each node:

   * **kubelet** runs the assigned Pods.
   * **kube-proxy** handles networking.
   * **Container Runtime** actually runs the containers inside Pods.

---

## 🖼️ Diagram – Kubernetes Components

Here is a simplified representation of Kubernetes architecture and components:

```
                    +-----------------------------+
                    |       Control Plane         |
                    |-----------------------------|
                    | - API Server                |
                    | - Scheduler                 |
                    | - Controller Manager        |
                    | - etcd (Key-Value Store)    |
                    +-------------+---------------+
                                  |
                   ----------------------------------------
                   |                 |                    |
         +---------+-----+ +--------+-------+ +-----------+------+
         | Worker Node 1 | | Worker Node 2  | | Worker Node 3     |
         |---------------| |----------------| |-------------------|
         | - kubelet     | | - kubelet      | | - kubelet         |
         | - kube-proxy  | | - kube-proxy   | | - kube-proxy      |
         | - Pod(s)      | | - Pod(s)       | | - Pod(s)          |
         |   - Container | |   - Container  | |   - Container     |
         | - Runtime     | | - Runtime      | | - Runtime         |
         +---------------+ +----------------+ +-------------------+
```

---

## ✅ Key Takeaways

| Concept                  | Summary                                                                 |
| ------------------------ | ----------------------------------------------------------------------- |
| **Cluster**              | Group of nodes managed together.                                        |
| **Master/Control Plane** | Manages the cluster — schedules, monitors, and maintains desired state. |
| **Worker Node**          | Server where actual containers (your apps) run.                         |
| **Pod**                  | Smallest unit in Kubernetes; contains one or more containers.           |
| **kubelet**              | Ensures containers in the Pod are running as expected.                  |
| **kube-proxy**           | Handles communication/networking inside and outside the cluster.        |
| **Container Runtime**    | Runs the actual containers.                                             |
---

## 🚀 What Can We Achieve with Kubernetes?

Kubernetes (K8s) provides powerful capabilities that solve many real-world challenges in running modern containerized applications.

---

### ✅ 1. **Container Orchestration**

* Automatically manages the **deployment, scaling, and lifecycle** of containerized applications.
* Assigns containers (Pods) to available nodes and ensures everything is running as expected.

---

### 🔄 2. **Scalability**

* Allows applications to **scale up or down** based on demand.
* Example:

  * Initially built for **100K users**, but as user base or functionality grows, Kubernetes helps scale your app **horizontally** (more replicas) or **vertically** (more resources).

**Benefit**: You don't have to worry about manual configuration or provisioning.

---

### 🔄 3. **Load Balancing**

* Distributes incoming traffic across multiple Pods or nodes.
* Ensures:

  * **No single server is overloaded**
  * **Low latency**
  * **High performance** even during peak traffic

**Benefit**: Prevents slow response times and crashes during high traffic.

---

### 🟢 4. **High Availability (HA)**

* Ensures **zero or near-zero downtime**.
* If one instance or node fails, **another replica takes over** automatically.
* Example:

  * If one server hosting your web app crashes, Kubernetes redirects traffic to another live instance.

**Benefit**: Your users can access your app **24/7 without interruption**.

---

### 🔁 5. **Rollouts and Rollbacks**

* **Rollouts**: Gradually deploy a new version of your app.
* **Rollbacks**: Instantly revert to a previous stable version if something breaks.

**Use Case**: When pushing updates or bug fixes, Kubernetes can:

* Deploy changes safely (canary or blue-green deployments)
* Roll back if issues are detected

**Benefit**: Helps in **safe and controlled releases** with **minimum risk**.

---

## 📋 Summary Table

| Feature                     | Description                                                         |
| --------------------------- | ------------------------------------------------------------------- |
| **Container Orchestration** | Automates container lifecycle (deploy, run, scale).                 |
| **Scalability**             | Adjust resources and replicas dynamically based on demand.          |
| **Load Balancing**          | Spreads traffic across multiple nodes/pods to optimize performance. |
| **High Availability**       | Ensures continuous uptime, even if parts of the system fail.        |
| **Rollouts & Rollbacks**    | Safely update or revert application versions without downtime.      |

---

### Useful commands for Kubernetes 

**Command to start your cluster** - `minikube start`

**Clean up any existing minikube installation** - `minikube delete`

**Set Docker as the default driver** - `minikube config set driver docker`

**Start minikube with Docker driver** - `minikube start --driver=docker`

**Verify installation**
`minikube status`
`kubectl get nodes`

**Start minikube dashboard** - `minikube dashboard`

**Check which cluster kubectl is currently using** - `kubectl config current-context`

**List all available contexts** - `kubectl config get-contexts`

**Switch between clusters as needed**
- `kubectl config use-context docker-desktop`    # For Docker Desktop cluster
- `kubectl config use-context minikube`          # For Minikube cluster

