
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

## ⚙️ Kubernetes with `kubectl` – Step-by-Step Summary

This section walks through **creating a Pod**, running an image, **exposing it as a service**, and **accessing it** via a browser.

---

### 🧱 1. **Understanding the Flow**

* A **Pod** runs one or more containers.
* A **Container** is a running instance of a Docker image.
* Before starting, you need a **Docker image** (e.g., `nginx`) to deploy.

---

### 🚀 2. **Deploying a Pod with `kubectl`**

Use `kubectl create deployment` to deploy an application using a Docker image:

```bash
kubectl create deployment my-nginx --image=nginx
```

* `my-nginx`: Name of the deployment.
* `nginx`: Image from Docker Hub.
* You can also specify a version using `nginx:1.25.1`, for example.

Check the deployment:

```bash
kubectl get deployments
```

Check the created Pod:

```bash
kubectl get pods
```

✅ **Result**: One deployment created → automatically creates a Pod → Pod runs the container from the image.

---

### 🖥️ 3. **Viewing Deployment in Dashboard (Minikube)**

To get a visual dashboard:

```bash
minikube dashboard
```

* View all objects: Deployments, Pods, services.
* See logs, events, image pulling status, resource usage, and more.

---

### 🌐 4. **Why We Can’t Directly Access the Pod**

Even though the Pod is running:

* The **Nginx container listens on port 80 inside the Pod**.
* You **cannot access it directly** from outside the cluster.

📌 Reason:

* Kubernetes Pod is isolated inside the cluster.
* You need a **Kubernetes Service** to expose it externally.

---

### 🌉 5. **Exposing the Pod using a Service**

Use this command to create a **LoadBalancer Service** to expose the deployment:

```bash
kubectl expose deployment my-nginx --port=80 --type=LoadBalancer
```

* `--port=80`: Port exposed from the container.
* `--type=LoadBalancer`: Makes the service reachable from outside the cluster.

Check the service:

```bash
kubectl get services
```

---

### 🌐 6. **Accessing the Application**

For **Minikube**, you must run this to open the exposed service:

```bash
minikube service my-nginx
```

✅ This will:

* Open the service in your default browser.
* Show the **default Nginx web page**, confirming your app is running.

---

## 📋 Recap of Commands Used

| Task                      | Command                                                            |
| ------------------------- | ------------------------------------------------------------------ |
| Create a deployment       | `kubectl create deployment my-nginx --image=nginx`                 |
| View deployments          | `kubectl get deployments`                                          |
| View Pods                 | `kubectl get pods`                                                 |
| View dashboard (Minikube) | `minikube dashboard`                                               |
| Expose deployment         | `kubectl expose deployment my-nginx --port=80 --type=LoadBalancer` |
| View services             | `kubectl get services`                                             |
| Access service in browser | `minikube service my-nginx`                                        |

---

## ✅ Key Concepts and Takeaways

| Concept          | Description                                                                          |
| ---------------- | ------------------------------------------------------------------------------------ |
| **kubectl**      | CLI tool to interact with the Kubernetes cluster.                                    |
| **Deployment**   | Manages creation and updates of Pods.                                                |
| **Pod**          | Smallest unit in K8s that runs containers.                                           |
| **Container**    | A running application instance, e.g., Nginx server.                                  |
| **Service**      | Provides a stable endpoint to access Pods; types: ClusterIP, NodePort, LoadBalancer. |
| **LoadBalancer** | Makes the application accessible from outside the cluster.                           |
| **Minikube**     | Lightweight K8s setup for local testing, includes dashboard & service tunneling.     |

---

* App editing
* Dockerfile creation
* Docker image creation & push
* Kubernetes deployment
* Viewing logs & details
* Exposing app via service

---

## 🔧 1. **Edit and Test the App**

* Modify your app file (e.g., change text like `This is a demo project for Docker`).
* Save the file and **restart** using `npm start`.
* This confirms your app works **before containerizing**.

---

## 🐳 2. **Create a Dockerfile**

Inside your app folder (`test-app`), create a file named `Dockerfile`:

```Dockerfile
FROM node:20
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
```

### Key Dockerfile Instructions:

* `FROM node:20`: Use official Node.js image.
* `WORKDIR /app`: Set working directory inside container.
* `COPY . .`: Copy everything to container.
* `RUN npm install`: Install dependencies.
* `CMD`: Start the app.

---

## 🏗️ 3. **Build Docker Image Locally**

Command:

```bash
docker build -t yourdockerhubusername/webapp-demo:02 .
```

### Notes:

* Use the proper **Docker Hub repo name**.
* `:02` is the version tag.
* The `.` means build from current directory (where Dockerfile is).

Verify image with:

```bash
docker images
```

---

## ☁️ 4. **Push Image to Docker Hub**

Steps:

1. Login to Docker:

   ```bash
   docker login
   ```
2. Push the image:

   ```bash
   docker push yourdockerhubusername/webapp-demo:02
   ```

Check the pushed image on Docker Hub to confirm.

---

## ☸️ 5. **Start Minikube and Create Deployment**

Start your local Kubernetes cluster (Minikube):

```bash
minikube start
```

Check cluster status:

```bash
minikube status
```

Create a Kubernetes deployment using the image you pushed:

```bash
kubectl create deployment my-web-app --image=yourdockerhubusername/webapp-demo:02
```

Verify deployment:

```bash
kubectl get deployments
kubectl get pods
```

---

## 🧹 6. **Optional: Clean Up Old Deployments**

To delete an existing deployment:

```bash
kubectl delete deployment my-nginx
```

---

## 📊 7. **Use Minikube Dashboard (UI Monitoring)**

To open the visual dashboard:

```bash
minikube dashboard
```

You can check:

* Pod status
* Image used
* Logs
* Events
* Health

---

## 📄 8. **Check Logs & Pod Details via Terminal**

To get logs:

```bash
kubectl logs <pod-name>
```

To describe a pod (get full details like IP, image, status):

```bash
kubectl describe pod <pod-name>
```

---

## 🌐 9. **Expose the App Using a Kubernetes Service**

Since the app runs inside a **Pod** (isolated), you can’t access it directly.
To access it via browser, expose it using a **LoadBalancer** service:

```bash
kubectl expose deployment my-web-app --type=LoadBalancer --port=3000
```

Check services:

```bash
kubectl get services
```

Use Minikube to open the exposed app in the browser:

```bash
minikube service my-web-app
```

This opens a working URL that runs your app.

---

## ✅ Final Recap of All Important Commands

| Task                      | Command                                                              |
| ------------------------- | -------------------------------------------------------------------- |
| Build Docker image        | `docker build -t <name>:<tag> .`                                     |
| Push image to Docker Hub  | `docker push <name>:<tag>`                                           |
| Start Minikube            | `minikube start`                                                     |
| Create deployment         | `kubectl create deployment <name> --image=<image>`                   |
| View deployments/pods     | `kubectl get deployments` / `kubectl get pods`                       |
| View logs                 | `kubectl logs <pod-name>`                                            |
| Describe a pod            | `kubectl describe pod <pod-name>`                                    |
| Expose service            | `kubectl expose deployment <name> --type=LoadBalancer --port=<port>` |
| Access service in browser | `minikube service <service-name>`                                    |
| Open Kubernetes dashboard | `minikube dashboard`                                                 |
| Delete a deployment       | `kubectl delete deployment <name>`                                   |
| Check services            | `kubectl get service`                                                |
| expose app in the browser | `minikube service my-web-app`                                        |
---

### 🚀 Updating, Rolling Out & Rolling Back Apps in Kubernetes — Quick Guide

| Step                                     | What Happens                                                                                                                              | Key `kubectl` / Docker Commands                                        | Why It Matters                                                      |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **1 Edit Code**                          | Change source (e.g., `app.js`).                                                                                                           | —                                                                      | Prep new app version.                                               |
| **2 Build New Image**                    | Use updated source to create container image.                                                                                             | `docker build -t <user>/<repo>:v5 .`                                   | Packages new code.                                                  |
| **3 Push Image**                         | Upload image to a registry (Docker Hub, ECR, etc.).                                                                                       | `docker push <user>/<repo>:v5`                                         | Makes image pull‑able by the cluster.                               |
| **4 Update Deployment (Rolling Update)** | Tell K8s to use the new image.                                                                                                            | `kubectl set image deployment/my-web-app webapp-demo=<user>/<repo>:v5` | Starts a **rolling update**.                                        |
| **5 Zero‑Downtime Behavior**             | • K8s spins up **new pod(s)** with `v5`.<br>• **Old pod(s)** continue serving until new pod Ready.<br>• When Ready, old pod(s) terminate. | `kubectl get pods` to watch; Dashboard shows old → new.                | Users see **no outage**.                                            |
| **6 Verify**                             | Confirm rollout finished.                                                                                                                 | `kubectl rollout status deployment/my-web-app`                         | Ensures update succeeded.                                           |
| **7 Switch Versions on Demand**          | Point back to any tag (e.g., `:v1`).                                                                                                      | Repeat **Step 4** with different tag.                                  | Easy version hopping.                                               |
| **8 Negative Test (Bad Image Tag)**      | Setting a non‑existent tag (e.g., `:v6`) causes **ImagePullBackOff**.                                                                     | `kubectl set image … :v6`<br>`kubectl get pods` → ImagePullBackOff     | New pod never becomes Ready; old pod keeps running (site stays up). |
| **9 Check Rollout Health**               | See why rollout is stuck.                                                                                                                 | `kubectl rollout status deployment/my-web-app`                         | Shows waiting on image pull.                                        |
| **10 Rollback**                          | Abort bad rollout and return to last good state.                                                                                          | `kubectl rollout undo deployment/my-web-app`                           | Restores service instantly.                                         |

---

#### 🔑 Important Concepts & Behaviours

* **Rolling Update (default strategy)**
  K8s gradually replaces pods; ensures *at least one* healthy replica stays available → **zero downtime**.

* **Readiness before Termination**
  Old pod is killed **only after** the new pod reports Ready.

* **Image Tags = Versions**
  Tag every image (e.g., `:v1`, `:v5`) so you can switch or rollback quickly.

* **Rollout Objects**
  Deployment keeps a *revision history*; `kubectl rollout history deployment/<name>` shows all versions.

* **Failure Handling**

  * Bad image → `ImagePullBackOff`; rollout stalls.
  * App crashloop → `CrashLoopBackOff`.
    In both cases you can `rollout undo`.

* **Dashboard & CLI parity**
  Everything you see in **Minikube Dashboard** (events, logs, container image) is available via CLI (`logs`, `describe`, `get events`).

---

### 🛠️ Command Cheat‑Sheet

```bash
# Build & push new image
docker build -t user/webapp-demo:v5 .
docker push user/webapp-demo:v5

# Rolling update to new image
kubectl set image deployment/my-web-app webapp-demo=user/webapp-demo:v5

# Watch rollout
kubectl rollout status deployment/my-web-app
kubectl get pods -w            # live view

# Rollback to previous revision
kubectl rollout undo deployment/my-web-app

# Show rollout history
kubectl rollout history deployment/my-web-app

# Troubleshoot a stuck pod
kubectl logs <pod>
kubectl describe pod <pod>
```

---

### 🖼️ Lifecycle Diagram (ASCII)

```
        ┌────────────┐                ┌────────────┐
        │  Old Pod   │  serve traffic │  Old Pod   │
        └─────┬──────┘                └─────┬──────┘
              │ Rolling update starts       │
              ▼                             ▼
        ┌────────────┐                ┌────────────┐
        │ New Pod    │---Ready?--No-->| Wait...     |
        │ Pull Image │                │ (Old stays) │
        └─────┬──────┘                └─────────────┘
              │ Ready? Yes
              ▼
        ┌────────────┐
        │ New Pod    │←─ now receives traffic
        └────────────┘
              │
              ▼ delete
        ┌────────────┐
        │ Old Pod    │ (terminated)
        └────────────┘
```

---

With these commands and behaviours you can **update, verify, and roll back** any Kubernetes‑managed application confidently—keeping production users happy and downtime at (virtually) **zero**.

---

## 🧩 1. **Handling Pod Failure (Self-Healing in Kubernetes)**

### 📌 Scenario:

You deploy a Node.js website on Kubernetes (in a pod). If the website crashes due to a code bug or unexpected error, what happens?

### ✅ Kubernetes Behavior:

* When a pod crashes or exits, **Kubernetes automatically detects it** and **restarts** the pod.
* This behavior is due to the **Deployment controller** and the default **restartPolicy: Always**.

### 🔍 Observations:

* If you visit the app URL after simulating a crash (`/exit` route), the pod status in the Dashboard shows red (error).
* Within seconds, it goes green again — showing the app restarted.
* `kubectl get pods` shows the **RESTART count increases** — evidence that the pod was restarted automatically.

---

## 🧱 2. **Why Single Pod is Risky**

### ❌ Problem:

* Even though Kubernetes restarts the app, there is **a few seconds of downtime** (while restarting).
* In **production**, **zero downtime is expected** — even a second matters.

---

## 🚀 3. **Scaling Applications**

### 📌 Goal:

Run **multiple instances (replicas)** of your app to:

* Ensure **no single point of failure**.
* Handle **high traffic via load balancing**.

### ✅ Solution: Horizontal Pod Scaling

**Command**:

```bash
kubectl scale deployment/<deployment-name> --replicas=4
```

### 🔍 What Happens:

* Kubernetes starts 4 pods for your app.
* All are identical (same image, config).
* LoadBalancer distributes traffic among them.

### 📈 Benefits:

* If one pod crashes, **others continue to serve traffic** → zero downtime.
* Great for **load balancing** when traffic spikes.
* Each pod handles a portion of traffic.

---

## ⚠️ 4. **Crash Simulation in Scaled Environment**

### 🔍 Test:

* If one pod crashes (via `/exit`), the others **still keep serving**.
* `kubectl get pods` shows one restarting, others running fine.
* You can still access the website without issues → zero disruption to users.

---

## 🧮 5. **Replica Status & Monitoring**

### `kubectl get pods`:

* Shows the **number of restarts** per pod.
* You can infer which pods are unstable or have restarted due to crashes.

---

## 🔁 6. **Reducing Scale (Downscaling)**

### 📌 Scenario:

If traffic is low or to save resources, reduce the number of pods.

### ✅ Command:

```bash
kubectl scale deployment/<deployment-name> --replicas=2
```

### 🔍 What Happens:

* Kubernetes terminates the extra pods.
* Only 2 pods keep running.
* You save compute, while maintaining redundancy.

---

## 🧠 7. **Key Kubernetes Concepts Recap**

| Concept            | Description                                                                                           |
| ------------------ | ----------------------------------------------------------------------------------------------------- |
| **Self-Healing**   | Kubernetes automatically restarts crashed pods.                                                       |
| **Deployment**     | Manages pod replicas and rollout logic.                                                               |
| **ReplicaSet**     | Ensures the desired number of pod replicas are running.                                               |
| **Scaling**        | `kubectl scale` lets you increase or decrease pod replicas.                                           |
| **Zero Downtime**  | Achieved by having multiple pods running concurrently.                                                |
| **Load Balancing** | Kubernetes services with `type=LoadBalancer` or `ClusterIP` + Ingress distribute traffic across pods. |
| **Monitoring**     | Use Dashboard or CLI (`get pods`, `describe`, `logs`) to inspect pod health and restarts.             |

---

## 🧪 Practical Commands

```bash
# Create deployment with public Docker image
kubectl create deployment node-app --image=flipkart/node-demo-app:v1

# Expose app as LoadBalancer service on port 3000
kubectl expose deployment node-app --type=LoadBalancer --port=3000

# View pod and service status
kubectl get pods
kubectl get services

# Simulate crash by hitting /exit route (if supported)

# Check rollout status
kubectl rollout status deployment/node-app

# Scale up/down app
kubectl scale deployment/node-app --replicas=4
kubectl scale deployment/node-app --replicas=2

# Check restarts to monitor crash loops
kubectl get pods
```

---

## ✅ Summary

| Feature                         | What It Solves                        | Benefit                          |
| ------------------------------- | ------------------------------------- | -------------------------------- |
| **Self-Healing**                | App crashes unexpectedly              | Auto-restart keeps app alive     |
| **Scaling**                     | Single pod is risky or traffic spikes | Adds redundancy & load balancing |
| **Rolling Updates**             | Deploying new version safely          | No user disruption               |
| **Monitoring & Restart Counts** | Debugging frequent crashes            | Better observability             |
| **Undo Rollout**                | Wrong version deployed                | Instant rollback                 |
| **Public Images via DockerHub** | Fast testing                          | Avoids local image builds        |

---

## start from (01:25:04)
