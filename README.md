
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

## ✅ **Kubernetes Deployment Using Configuration Files (`YAML`)**

Instead of manually executing many `kubectl` commands, you can **define your entire Kubernetes application in declarative YAML configuration files**, which improves maintainability and scalability.

---

## 📁 **1. What is a Deployment Config File?**

A **Deployment YAML** is used to define:

* Number of replicas (pods).
* Pod template.
* Container specs (image, name, ports).
* Metadata (name, labels).

### 🧩 **Key Fields in `deployment.yaml`:**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-node-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: node-app
  template:
    metadata:
      labels:
        app: node-app
    spec:
      containers:
        - name: node-container
          image: your-dockerhub/image-name:tag
```

### 💡 Notes:

* You can **change the number of replicas** anytime by just updating the YAML and re-applying.
* Use `kubectl apply -f deployment.yaml` to create/update the deployment.

---

## ⚙️ **2. Benefits of Configuration Files**

* **Centralized changes**: All configs (replicas, versions, labels) are managed in one place.
* **Easy scaling**: Update replicas in YAML and re-apply.
* **Versioning**: Update image version in YAML to rollout new changes.
* **Error handling**: You can monitor failed pod creation, e.g., image not found, via dashboard/events.

---

## 🌐 **3. Creating a Kubernetes Service**

To expose your pods to external traffic, you need to create a **Service**.

### 🧩 **Service YAML Example:**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-node-service
spec:
  type: LoadBalancer
  selector:
    app: node-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 3000
```

### 💡 Notes:

* `selector`: Must match pod labels (e.g., `app: node-app`).
* `type: LoadBalancer`: Exposes your service on an external IP.
* `port` is what users access, `targetPort` is the container’s internal port (e.g., 3000).

### 📌 Command to apply:

```bash
kubectl apply -f service.yaml
```

---

## 📊 **4. Monitoring and Debugging**

* Use:

  * `kubectl get pods`
  * `kubectl get deployments`
  * `kubectl get services`
  * `kubectl describe pod <pod-name>` for detailed info/events.
* If the image tag is wrong or doesn't exist, the pod will fail to start — fix the YAML and re-apply.

---

## 🔁 **5. Updating and Rolling Back**

* Update replicas/image version → `kubectl apply -f deployment.yaml`
* Kubernetes will **gracefully rollout the changes**.
* You can monitor rollout using:

```bash
kubectl rollout status deployment/my-node-app
```

---

## 🧪 **6. Testing Failure Handling (Self-Healing)**

* If your container crashes (`exit` or error), Kubernetes **auto-restarts the pod**.
* This is part of Kubernetes' **self-healing** behavior.
* You can verify restart behavior with:

```bash
kubectl get pods
```

---

## 🗑️ **7. Deleting Deployments and Services**

Use the same config file to delete resources:

```bash
kubectl delete -f deployment.yaml
kubectl delete -f service.yaml
```

---

## 📘 **8. Where to Find YAML Examples?**

Use the official Kubernetes documentation:

* [https://kubernetes.io/docs/](https://kubernetes.io/docs/)
* Especially helpful: [API Reference](https://kubernetes.io/docs/reference/generated/kubernetes-api/)

Under “Reference” you can find:

* Deployments → `apps/v1`
* Services → `v1`

Copy official examples and adjust to your needs.

---

## ✅ Summary of Key Kubernetes Concepts:

| Concept            | Summary                                           |
| ------------------ | ------------------------------------------------- |
| Deployment         | Manages replicas of pods (versioned and scalable) |
| Service            | Exposes pods, allows communication                |
| `kubectl apply -f` | Applies changes from YAML                         |
| `replicas`         | Number of pod instances                           |
| Self-healing       | Auto restarts crashed pods                        |
| `selector`         | Binds service to specific pods                    |
| Dashboard          | Visual tool to check pod/service status           |
| Image pull errors  | Occur if wrong image name or version              |
| Config-driven      | Easier to manage than CLI-only deployments        |

---

### Imp References

[Kubernetes One-page API Reference](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.33/)

[Deployment v1 apps](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.33/#deployment-v1-apps)

[Service](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.33/#service-apis)
---

## 🧠 **Goal:**

Deploy a Node.js app and MongoDB **together inside the same Pod** using Kubernetes.

---

## ✅ **Two Ways to Run Multiple Containers:**

### 1. **Multiple Containers in the Same Pod**

* **Shared environment** (network, volumes).
* **Easy inter-container communication.**
* Good for tightly coupled apps (like Node.js app + MongoDB).

### 2. **Separate Containers in Different Pods**

* Need **inter-pod communication** via Services.
* Useful for **scaling independently** or **decoupling** services.

---

## 🛠️ **Approach Used in This Example:**

Deploy both containers (Node.js app + MongoDB) **in the same Pod** using a single Deployment YAML.

---

## 🔹 **Images Used:**

* `pulpfibs/node-mongo-db:0.2` → Node.js App
* `mongo:latest` → MongoDB

---

## 📄 **Deployment YAML Breakdown:**

### Basic Structure:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-node-db-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: node-db-app
  template:
    metadata:
      labels:
        app: node-db-app
    spec:
      containers:
        - name: node-app
          image: pulpfibs/node-mongo-db:0.2
        - name: mongo-db
          image: mongo
```

### 🔑 Key Points:

* **Two containers** defined inside the `containers` array.
* Containers **share resources**.
* **No special networking setup** required inside the Pod.
* `replicas: 2` → Two Pods will run.

---

## 🔧 **Service YAML (to expose Node.js app):**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-node-db-service
spec:
  selector:
    app: node-db-app
  ports:
    - port: 8080
      targetPort: 3000
  type: NodePort
```

### Notes:

* Exposes the app on **port 8080**.
* Internally routes to **Node.js container** on **port 3000**.

---

## 🚀 **Commands Used:**

### Apply deployment:

```bash
kubectl apply -f deployment.yaml
```

### Apply service:

```bash
kubectl apply -f service.yaml
```

### Access via Minikube:

```bash
minikube service my-node-db-service
```

---

## 🧪 **Testing Application Behavior:**

### Issue with Multiple Replicas:

* **Each Pod** has its **own MongoDB instance** (because it's not using a shared volume or external DB).
* So, **data isn't shared** across Pods.
* Example:

  * First request → goes to Pod 1 → stores data in its MongoDB.
  * Next request → goes to Pod 2 → its MongoDB doesn’t have the data.

### Solution:

* For real use-cases:

  * **Separate MongoDB to another Pod or external DB** (not inside app Pod).
  * Use **Persistent Volumes** to share storage across Pods.

---

## 🧹 **Simplification – Combined YAML:**

You can **combine deployment and service** in one YAML using `---` separator:

```yaml
# Deployment definition here

---

# Service definition here
```

### Benefit:

* Apply both using one command:

```bash
kubectl apply -f combined.yaml
```

---

## ✅ Final Observations:

| Concept                    | Description                                                                 |
| -------------------------- | --------------------------------------------------------------------------- |
| Same Pod                   | Good for tightly coupled containers (e.g., app + sidecar DB in development) |
| Multiple Pods with same DB | Can cause **data inconsistency** without shared volume                      |
| Services                   | Used to expose Pods and load-balance across replicas                        |
| Minikube                   | Handy for local testing and accessing services                              |
| Combined YAML              | Helps manage resources efficiently using one file                           |

---

- Command to run app from container :- `docker run --network my-net -p 3000:3000 --name myapp philippaul/node-mongo-db:01`

---

## ✅ **Goal:**

* Deploy **Node.js Web App** and **MongoDB** in **separate Pods**.
* Enable communication between them using **Kubernetes Services** and **environment variables**.

---

## 🔁 **Comparison with Previous Approach:**

* Earlier: Node + MongoDB in the **same Pod**, communicating via `localhost`.
* Now: Node and MongoDB in **separate Pods**, so need to use **service name + port** for communication.

---

## 🔄 **Steps Overview:**

### 1. **Modify Node.js App to Use Environment Variables**

In `index.js`, instead of hardcoding MongoDB connection:

```js
const mongoHost = process.env.MONGO_HOST || 'localhost';
const mongoPort = process.env.MONGO_PORT || '27017';

mongoose.connect(`mongodb://${mongoHost}:${mongoPort}/your-db-name`);
```

### ✅ Benefit:

* Makes MongoDB connection **dynamic**.
* Can pass environment variables **at deployment time**.

---

### 2. **Build and Push New Docker Image**

* Update app to use `MONGO_HOST`, `MONGO_PORT`.
* Build the image with a new version tag:

  ```bash
  docker build -t your-dockerhub-username/node-mongo-db:0.3 .
  docker push your-dockerhub-username/node-mongo-db:0.3
  ```

---

### 3. **Create Separate Deployment & Service for MongoDB**

#### Example `mongo.yaml` (Deployment + Service):

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: mongo-app
  template:
    metadata:
      labels:
        app: mongo-app
    spec:
      containers:
        - name: mongo
          image: mongo
          ports:
            - containerPort: 27017
---
apiVersion: v1
kind: Service
metadata:
  name: mongo-service
spec:
  selector:
    app: mongo-app
  ports:
    - port: 27017
      targetPort: 27017
  type: ClusterIP
```

### ✅ Notes:

* `mongo-service` will be used as **hostname** by Node app.
* Port remains **27017**.
* `type: ClusterIP` is enough for internal Pod-to-Pod communication.

---

### 4. **Create Deployment & Service for Node App**

#### Example `node.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: node-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: node-app
  template:
    metadata:
      labels:
        app: node-app
    spec:
      containers:
        - name: node-web
          image: your-dockerhub-username/node-mongo-db:0.3
          ports:
            - containerPort: 3000
          env:
            - name: MONGO_HOST
              value: "mongo-service"
            - name: MONGO_PORT
              value: "27017"
---
apiVersion: v1
kind: Service
metadata:
  name: node-service
spec:
  selector:
    app: node-app
  ports:
    - port: 8080
      targetPort: 3000
  type: NodePort
```

---

## 🧠 **Key Concepts Recap:**

| Concept                | Description                                                                  |
| ---------------------- | ---------------------------------------------------------------------------- |
| `localhost`            | Works only inside the same Pod. Fails in cross-Pod communication.            |
| `process.env.VARIABLE` | Used to inject runtime config into containers via environment variables.     |
| `ClusterIP` Service    | Default type for internal communication between Pods.                        |
| `NodePort` Service     | Exposes app to the outside world (via Minikube/Node IP).                     |
| `env` in YAML          | Used to pass environment variables to the container.                         |
| Image Tags             | Always increment version (`0.1`, `0.2`, `0.3`) when pushing to Docker Hub.   |
| Service Discovery      | Kubernetes lets Pods discover each other via **service names as DNS names**. |

---

## 🧪 **Testing and Validation:**

1. Apply Mongo deployment + service:

   ```bash
   kubectl apply -f mongo.yaml
   ```

2. Apply Node app deployment + service:

   ```bash
   kubectl apply -f node.yaml
   ```

3. Verify everything is running:

   ```bash
   kubectl get pods
   kubectl get services
   ```

4. Access app using:

   ```bash
   minikube service node-service
   ```

---

## ✅ Conclusion:

You now understand how to:

* Separate concerns using different Pods.
* Enable inter-Pod communication using Kubernetes Services.
* Use **environment variables** for **configurable connections**.
* Combine deployments and services in a single file using `---`.

---

## ✅ **Goal Recap:**

Run a **multi-container application** (Node.js + MongoDB) in **separate Pods** using:

* **Kubernetes Deployments & Services**
* **Environment Variables via ConfigMaps**
* **Docker image builds & versioning**
* **Troubleshooting crash issues**
* **Minikube Dashboard** for validation

---

## 🔄 **Key Concepts and Steps**

### 1. 🔧 **Using `ConfigMap` for Environment Variables**

* Instead of hardcoding DB host and port in code, use **ConfigMap** to inject environment variables.

#### ✅ Example: `mongo-config.yaml`

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: mongo-config
data:
  MONGO_HOST: "service-mongo-db"
  MONGO_PORT: "27017"
```

* This defines key-value pairs usable as **environment variables** in your deployments.

---

### 2. 🌐 **Injecting ConfigMap into Deployment**

In your **Node.js Deployment**, inject values from `mongo-config`:

```yaml
env:
  - name: MONGO_HOST
    valueFrom:
      configMapKeyRef:
        name: mongo-config
        key: MONGO_HOST
  - name: MONGO_PORT
    valueFrom:
      configMapKeyRef:
        name: mongo-config
        key: MONGO_PORT
```

✅ This makes the Node app connect to MongoDB using values like:

```js
process.env.MONGO_HOST
process.env.MONGO_PORT
```

---

### 3. 📦 **Build & Push New Docker Image**

After fixing issues in the code:

```bash
docker build -t your-repo/node-app:0.4 .
docker push your-repo/node-app:0.4
```

* Update deployment to use the new image version (`0.4`).

---

### 4. 🐞 **Troubleshooting Common Issues**

#### 🔴 CrashLoopBackOff Problem:

* Usually due to bad ENV values or image config.
* Use the **Kubernetes Dashboard** or command line:

```bash
kubectl describe pod <pod-name>
```

* Check **Events** at the bottom for error messages.

#### Fix Example:

* Problem: Using incorrect quotes for environment variables in code.
* Solution: Use proper syntax like `process.env.VARIABLE`, not `'${VARIABLE}'`.

---

### 5. 📈 **Scaling the App (Replica Sets)**

You can scale the Node.js app to multiple instances:

```yaml
spec:
  replicas: 2
```

* Now 2 Pods will run, sharing the load.
* You’ll see 3 Pods total: 2 Node.js, 1 MongoDB.

---

### 6. 🌐 **Testing with Minikube**

Start your Node.js service:

```bash
minikube service node-app-service
```

Then, in the browser:

* Use the Web UI to add some data (like an email).
* Even if one Node Pod crashes, the app remains available thanks to **replica sets**.

---

### 7. 🧠 **Concepts Covered in This Walkthrough**

| Concept                          | Description                                                                       |
| -------------------------------- | --------------------------------------------------------------------------------- |
| **ConfigMap**                    | Stores non-sensitive key-value configuration (e.g. DB host, port)                 |
| **Environment Variables**        | Dynamically passed to containers during deployment                                |
| **Service Name as DNS**          | Services can be reached using their name inside the cluster                       |
| **CrashLoopBackOff**             | Pod keeps restarting due to runtime/config error                                  |
| **ReplicaSet Scaling**           | Ensures high availability by running multiple replicas                            |
| **Minikube Dashboard**           | Visual tool to inspect running resources and logs                                 |
| **Dynamic Docker Image Tagging** | Use versioned tags (`v0.3`, `v0.4`) for clarity and rollback                      |
| **kubectl apply -f**             | Used to apply any Kubernetes resource file (Deployment, Service, ConfigMap, etc.) |

---

### ✅ Final Outcome:

* **Node.js app** and **MongoDB** run in **separate pods**.
* Communication enabled using:

  * Kubernetes **Services** (`ClusterIP`)
  * **Environment variables** passed via **ConfigMap**
* Errors resolved using **Dashboard troubleshooting**
* App scaled and verified using **Minikube service + browser**

---

## ✅ **Context Recap**

You deployed a project with:

* A **Node.js web app**
* A **MongoDB database**
* Each running in **separate pods**
* Using **Minikube and Kubernetes**

### 🧪 Problem Observed:

When you updated the **MongoDB image version**, the **previous data was lost**, even though the app was still running fine.

---

## 🔍 **Why Was the Data Lost?**

* MongoDB was storing data **inside the container** (ephemeral storage).
* When the **pod was recreated** (due to version update or crash), a **new container** was launched with a clean slate.
* Kubernetes restarts the pod, but **container storage is destroyed** unless explicitly persisted.

---

## 💡 Solution: Use Volumes to Persist Data

### 1. ⚙️ **Volumes Inside Pod**

* You can mount a **volume inside the pod**, and tell MongoDB to use it.
* This helps **retain data even if the container restarts**.

🟡 But: If the whole **pod is recreated**, even this volume is lost — because it’s **pod-scoped**.

---

### 2. 🛠️ **Persistent Volumes (PV)**

* Persistent Volume = A **cluster-level storage resource**.
* Lives **outside any specific pod or container**.
* Independent of pod lifecycle: **persists data across pod deletions, crashes, upgrades**.

### 🔹 Diagram Concept:

```
+-----------------+         +-----------------+
|   MongoDB Pod   |         | PersistentVolume|
|  Uses PVC claim |<------->|  (Cluster Level)|
+-----------------+         +-----------------+
```

---

## 🧱 Components to Use for Persistent Storage

### 🔸 1. **PersistentVolume (PV)**

* A storage unit **defined at the cluster level**.
* Can use:

  * HostPath (local disk)
  * Cloud storage (EBS, GCE, AzureDisk)
  * NFS, GlusterFS, etc.

### 🔸 2. **PersistentVolumeClaim (PVC)**

* Pods **request storage** using a PVC.
* PVC claims a matching PV based on requirements (like storage size, access mode).

---

## 🛑 Benefits of Persistent Volumes

| Benefit                   | Description                                                       |
| ------------------------- | ----------------------------------------------------------------- |
| **Pod Resilience**        | Data persists even if pods/containers are restarted or replaced   |
| **Version Upgrades Safe** | You can safely upgrade MongoDB image/version                      |
| **Scalable**              | Multiple containers can share same volume if needed               |
| **Cloud-Ready**           | Supports integration with AWS/GCP/Azure for durable cloud storage |
| **Flexibility**           | Choose local or remote volumes as per your architecture needs     |

---

## 🧪 Types of Volumes in Kubernetes

| Type                       | Description                                                          |
| -------------------------- | -------------------------------------------------------------------- |
| **Ephemeral Volume**       | Lives **only for the lifetime of a pod** (e.g. `emptyDir`)           |
| **Persistent Volume (PV)** | Exists **independent of pod**, manually defined                      |
| **PVC (Claim)**            | Bridge between pod and PV, used to "claim" the storage               |
| **Cloud Volumes**          | Provided by cloud services like AWS EBS, AzureDisk                   |
| **HostPath**               | Maps a local path from the host machine (used in Minikube/local dev) |

---

## 🆚 Ephemeral vs Persistent Volume

| Feature            | Ephemeral Volume    | Persistent Volume     |
| ------------------ | ------------------- | --------------------- |
| Lifetime           | Tied to Pod         | Independent           |
| Use Case           | Caching, temp files | Databases, user files |
| Survives Pod Crash | ❌ No                | ✅ Yes                 |
| Used via PVC       | ❌ No                | ✅ Yes                 |

---

## 🛠️ Next Steps (Practical Guide Summary)

To fix your MongoDB data loss issue:

1. ✅ **Create a PersistentVolume** (e.g. 1Gi storage).
2. ✅ **Create a PersistentVolumeClaim** requesting storage.
3. ✅ **Mount the PVC in your MongoDB pod’s `volumeMounts`**.
4. ✅ **Update MongoDB to store `/data/db` in this mounted path**.
5. ✅ Now even if the Mongo pod is deleted, your data stays.

---

## 🧾 Additional Resources

* Official Kubernetes Docs:
  [Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
* Types of volumes: \[`emptyDir`, `hostPath`, `nfs`, `awsElasticBlockStore`, etc.]

---

### Imp Reference:
[Kubernete's Volumes](https://kubernetes.io/docs/concepts/storage/volumes/)

---

## 🧩 **Kubernetes Persistent Volume Setup Summary**

### 🔹 1. **What is a Persistent Volume (PV)?**

* A **Persistent Volume (PV)** is a piece of storage in a Kubernetes cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes.
* It allows **data to persist** beyond the lifecycle of a Pod.

---

## ⚙️ **Step-by-Step Implementation**

### ✅ Step 1: **Create a Persistent Volume (PV)**

**File:** `host-pv.yaml`

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: host-pv
spec:
  capacity:
    storage: 1Gi
  volumeMode: Filesystem
  storageClassName: standard
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: /data
    type: DirectoryOrCreate
```

**Key Points:**

* `storage: 1Gi` — Amount of disk space.
* `volumeMode: Filesystem` — Data stored as files.
* `accessModes: ReadWriteOnce` — Only one node can mount the volume at a time.
* `hostPath` — Stores data directly on the host at `/data`. For **local testing only**.

---

### ✅ Step 2: **Create a Persistent Volume Claim (PVC)**

**File:** `host-pvc.yaml`

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: host-pvc
spec:
  storageClassName: standard
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

**Key Point:**

* The PVC **claims 1Gi storage** from the PV.
* `storageClassName` must match the PV.

---

### ✅ Step 3: **Use PVC in Deployment (MongoDB Example)**

In your MongoDB Deployment YAML, you need to **mount the volume**.

```yaml
...
spec:
  containers:
    - name: mongo
      image: mongo
      volumeMounts:
        - name: mongo-vol
          mountPath: /data/db
  volumes:
    - name: mongo-vol
      persistentVolumeClaim:
        claimName: host-pvc
```

**Explanation:**

* `/data/db` is the default path MongoDB uses to store data.
* We’re mounting the claimed volume (`host-pvc`) to this path.

---

## 📋 Commands Used

### ✅ Apply configurations:

```bash
kubectl apply -f host-pv.yaml
kubectl apply -f host-pvc.yaml
kubectl apply -f mongo-deployment.yaml
```

### ✅ Verify PV and PVC:

```bash
kubectl get pv
kubectl get pvc
```

---

## 🧪 Testing the Setup

### 1. Add data to the MongoDB app via frontend (e.g., email entries).

### 2. Delete MongoDB deployment:

```bash
kubectl delete deployment mongo
```

### 3. Re-deploy MongoDB:

```bash
kubectl apply -f mongo-deployment.yaml
```

### 4. ✅ Data is still available – proves **persistent storage works!**

---

## 🧠 Other Notes and Learnings

| Concept                      | Explanation                                                              |
| ---------------------------- | ------------------------------------------------------------------------ |
| `hostPath`                   | Good for **local testing** only. Not recommended in multi-node clusters. |
| `ReadWriteOnce`              | Suitable for single-node clusters.                                       |
| `storageClassName: standard` | Default dynamic provisioner in Minikube.                                 |
| Volume Mount Path            | Depends on the container image (e.g., `/data/db` for MongoDB).           |
| Dashboard Access             | You can verify volumes, claims, pods from **Minikube dashboard**.        |
| Restart Testing              | Stopping and restarting Minikube should not delete data.                 |

---

## ⚠️ Limitations of `hostPath`

* **Only for local, single-node clusters.**
* Will **not work** in production or multi-node setups.
* Kubernetes **recommends alternatives** like:

  * `local` volume (safer alternative).
  * Cloud-based volumes:

    * AWS EBS
    * Azure Disks/Files
    * GCE Persistent Disks
    * NFS

You can find them in Kubernetes documentation under [Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/).

---

## ✅ Final Takeaway

> **Persistent Volumes are crucial for storing stateful data** like database content that must not be lost when pods restart or crash.

Using PVC + PV correctly ensures your **data survives across pod restarts, cluster restarts, and redeployments** — essential for real-world applications.

---

## 🧩 **Kubernetes Volume Concepts Explained**

### 1. **Types of Volumes Overview**

Kubernetes supports multiple volume types. A few important ones discussed:

---

### ✅ **1. `emptyDir` Volume**

* **What it is**: A temporary directory created when a pod is assigned to a node.
* **Use case**: Scratch space, temp files, caching.
* **Data Lifetime**:

  * Data exists **only as long as the pod is running**.
  * If the pod is removed or restarted, **data is permanently lost**.
* **Similar to** Docker-managed volumes (anonymous volumes).

---

### ✅ **2. `hostPath` Volume**

* **What it is**: Mounts a **file or directory from the host node’s file system** into the pod.
* **Use case**:

  * Temporary files.
  * Internal libraries/tools stored on the host.
* **Behavior**:

  * Data is stored on the **host node**, so it's available to any pod on the same node.
* **Security Warning**:

  * **Not recommended** for most use cases due to security concerns.
  * Node-level access can lead to vulnerabilities.

---

### ✅ **Practical Example – Node File App Project**

* **App**: Node.js app that stores submitted emails in a file instead of a database.
* **Frontend**: Simple UI with an input for email and a "Show Emails" button.
* **Storage**:

  * Uses a file (`emails.txt`) instead of a DB.
  * Initially stored inside the container => **data lost on pod restart**.

---

### ✅ **Problem Observed**

* Without persistent volume:

  * When the pod is **deleted or restarted**, the new container does **not retain previous emails**.
  * Reason: File storage was inside the container (ephemeral).

---

## 🛠️ **Fix: Adding `hostPath` for Persistence**

### Changes made in the Kubernetes deployment config:

```yaml
volumes:
  - name: my-vol
    hostPath:
      path: /mydata
      type: DirectoryOrCreate
```

```yaml
volumeMounts:
  - name: my-vol
    mountPath: /app
```

* **`hostPath` path**: `/mydata` on the node.
* **`mountPath`** inside the container: `/app` (project root).
* This ensures that the `emails.txt` file is written to **node's disk**, not inside the container.

---

### ✅ **Dockerfile Reminder**

* Working directory was set as:

```dockerfile
WORKDIR /app
```

* Important: Must match the **`mountPath`** in the volume config.

---

### ✅ **Persistence Test**

1. Restarted the application (deleted pods + redeployed).
2. Verified that previously saved emails were still accessible after pod restart.
3. Confirms that **data persisted at the node level**.

---

## 🔁 **Flow Summary**

1. Node.js app saves emails in a file.
2. Initially saved in container — **lost on restart**.
3. Used `hostPath` to mount node-level directory.
4. Now, data persists across pod restarts and deployments.

---

## 📌 Key Takeaways

| Concept                  | Details                                                         |
| ------------------------ | --------------------------------------------------------------- |
| `emptyDir`               | Temporary storage, lost on pod restart                          |
| `hostPath`               | Mounts host node directory into pod                             |
| Docker Working Directory | Must align with volume's `mountPath`                            |
| Volume Mounts            | Ensure container uses node storage instead of ephemeral storage |
| Data Persistence         | Achieved by writing to node (`hostPath`)                        |

---
