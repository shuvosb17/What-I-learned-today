# BUILDING SYSTEMS WITH GO AND AWS — Organized Syllabus

Structured by **Milestones → Modules → Topic/Problem lists**.

---

## Milestone 1: LeetCode Problem Solving Foundations with Go

<details>
<summary><strong>Module 1: Arrays & Strings (Core Patterns)</strong></summary>

- Extract Digits from a Given Number  
- Count Digits from a Given Number  
- Reverse Integer (LeetCode)  
- Palindrome Number (LeetCode)  
- Armstrong Number  
- Sum of All the Divisors of a Given Number  
- Prime Number  
- GCD (Greatest Common Divisor)  
- Complexity (Time & Space)

</details>

<details>
<summary><strong>Module 2: Hashing & Strings</strong></summary>

- Two Sum  
- Valid Anagram  
- Group Anagrams  
- Product of Array Except Self  
- Longest Substring Without Repeating Characters  
- Minimum Window Substring  
- Longest Palindromic Substring  
- Combination Sum  
- Combination Sum II

</details>

<details>
<summary><strong>Module 3: Sliding Window</strong></summary>

- Sliding Window Core Concepts  
- Fixed-size Window Pattern  
- Variable-size Window Pattern  
- Common Sliding Window Templates  
- Practice Set (to be added with links)

</details>

<details>
<summary><strong>Module 4: Linked Lists</strong></summary>

- Merge Two Sorted Lists  
- Design Linked List  
- Middle of Linked List  
- Delete the Middle Node of a Linked List  
- Remove Nth Node From End of List  
- Design Browser History  
- Reverse Linked List  
- Reorder List  
- LRU Cache  
- Linked List Cycle  
- Linked List Cycle II  
- Find the Duplicate Number  
- Intersection of Two Linked Lists  
- Add Two Numbers

</details>

<details>
<summary><strong>Module 5: Stacks & Queues</strong></summary>

- Valid Parentheses  
- Sliding Window Maximum  
- Stock Span Problem

</details>

<details>
<summary><strong>Module 6: Trees & BST</strong></summary>

- Maximum Depth of Binary Tree  
- Invert Binary Tree  
- Binary Tree Level Order Traversal  
- Symmetric Tree  
- Validate BST  
- Lowest Common Ancestor of BST  
- Construct a Binary Tree from Preorder and Inorder

</details>

<details>
<summary><strong>Module 7: Graphs, BFS & DFS</strong></summary>

- Number of Islands  
- Clone Graph  
- Course Schedule  
- Word Search

</details>

<details>
<summary><strong>Module 8: Dynamic Programming</strong></summary>

- Decode Ways  
- Unique Paths  
- Longest Increasing Subsequence  
- Word Break

</details>

<details>
<summary><strong>Module 9: Heaps & PQ / Small Design</strong></summary>

- Kth Largest Element in Array  
- LRU Cache  
- Min Stack

</details>

<details>
<summary><strong>Module 10: Recursion & Backtracking</strong></summary>

- How General Function Call Works  
- How Recursive Function Call Works  
- Printing Numbers in Range  
- Sum of First N Numbers  
- (H.W) Factorial / Multiplication of First N Numbers  
- Reverse an Array  
- Check Palindrome String  
- Fibonacci Number  
- Subsets  
- Combination Sum  
- Word Search

</details>

<details>
<summary><strong>Module 11: Sorting & Searching</strong></summary>

- Merge Intervals  
- Find Minimum in Rotated Sorted Array  
- Search in Rotated Sorted Array  
- Merge Two Sorted Lists

</details>

---

## Milestone 2: Linux & Networking Foundations

<details>
<summary><strong>Module 12: Linux Networking Stack</strong></summary>

- IP Address, CIDR, Namespace  
- Layer 2 Networking (Bridge & Switch)  
- Layer 3 Networking (Router, FIB)

</details>

<details>
<summary><strong>Module 13: Iptables, Chain & Actions</strong></summary>

- iptables Rules, Targets, and Policies  
- iptables Chains, Tables

</details>

<details>
<summary><strong>Module 14: Container Network Namespace</strong></summary>

- Network Namespace Inspecting  
- Connect Network Namespace to Host  
- Connect Network Namespace to Root  
- Egress Traffic  
- Connect Two Custom Network Namespaces  
- Bridge Networking Among Namespaces  
- Process Communication Between Namespaces

</details>

<details>
<summary><strong>Module 15: Overlay Networking (VXLAN)</strong></summary>

- VXLAN for Overlay Networking  
- VXLAN with IPAM  
- FDB with VXLAN

</details>

<details>
<summary><strong>Module 16: Networking Basics with Mininet</strong></summary>

- Two-Subnet Network Topology with Routing using Mininet  
- Simulating a Simple Network with Mininet

</details>

---

## Milestone 3: Docker for Go Engineers

<details>
<summary><strong>Module 17: Docker Fundamentals from Kernel</strong></summary>

- Understand docker, containerd, and how containers run  
- Hands-on: docker info, docker version, inspect Docker socket

</details>

<details>
<summary><strong>Module 18: Build and Run Your First Image</strong></summary>

- Create a simple Go RestAPI app  
- Build with Dockerfile, run with `docker run`  
- Use `ENTRYPOINT` and `CMD`

</details>

<details>
<summary><strong>Module 19: Container Networking Modes</strong></summary>

- Inspect default bridge network  
- Run containers in host mode  
- Hands-on: `docker network inspect`, `docker run --network`

</details>

<details>
<summary><strong>Module 20: Run Containers with CPU and Memory Limits</strong></summary>

- Use flags like `--cpus`, `--memory`, `--memory-swap`  
- Measure effects with `docker stats`

</details>

<details>
<summary><strong>Module 21: Docker Remote API and Secure Access</strong></summary>

- Enable Docker remote API on worker nodes  
- Authenticate and test API using curl and Python requests

</details>

<details>
<summary><strong>Module 22: Build a Container Launcher Agent</strong></summary>

- Expose a FastAPI app that runs containers via Docker SDK/CLI  
- Launch containers dynamically using POST requests

</details>

<details>
<summary><strong>Module 23: Mount Volumes and Pass Env Vars</strong></summary>

- Learn `-v`, `--mount`, `-e`, `--env-file`  
- Mount secrets/configs for deployed apps

</details>

<details>
<summary><strong>Module 24: Collect Container Metrics with cAdvisor</strong></summary>

- Run cAdvisor as a sidecar  
- Explore metrics available via `/metrics`

</details>

<details>
<summary><strong>Module 25: View Resource Usage with Docker Stats</strong></summary>

- Use `docker stats`, `docker inspect` for runtime usage  
- Export data for Prometheus/visualization

</details>

<details>
<summary><strong>Module 26: Docker Compose for Multi-Service Apps</strong></summary>

- Hands-on: `depends_on`, networks, volumes

</details>

<details>
<summary><strong>Module 27: Docker Image Optimization</strong></summary>

- Multi-stage builds  
- Reduce image size (alpine, `.dockerignore`)

</details>

<details>
<summary><strong>Module 28: Push and Pull from DockerHub / ECR</strong></summary>

- Authenticate and push your scheduler container  
- Automate build + push using GitHub Actions

</details>

---

## Milestone 4: Build Docker from Scratch in Go

<details>
<summary><strong>Module 29: Project Bootstrap & Process Execution Basics</strong></summary>

- Initialize Go project + CLI structure  
- `mydocker run <cmd>` skeleton  
- Logging & error handling structure  
- Run commands using `os/exec`  
- Redirect stdin/stdout/stderr  
- Build a simple CLI wrapper around executing a command

</details>

<details>
<summary><strong>Module 30: Create New Linux Namespaces</strong></summary>

- `syscall.Unshare()` / `unix.CLONE_NEW*` flags  
- Create isolated PID + UTS namespace  
- Run a cmd with its own hostname

</details>

<details>
<summary><strong>Module 31: Build PID Namespace + Child Reaper</strong></summary>

- Parent Go process spawns isolated child  
- Parent becomes init for namespace  
- Reap zombie processes

</details>

<details>
<summary><strong>Module 32: Add UTS, IPC, Network, Mount Namespaces</strong></summary>

- Combine multiple namespace flags  
- Verify isolation with `ip a`, `hostname`, `/proc`

</details>

<details>
<summary><strong>Module 33: Implement Root Filesystem Isolation</strong></summary>

- Download busybox/alpine rootfs tar  
- Extract to `/var/lib/mydocker/rootfs`  
- `pivot_root` or `chroot` to switch root  
- Inside container run `/bin/sh`, `ls`, `echo`

</details>

<details>
<summary><strong>Module 34: Implement cgroups (CPU & Memory Limits)</strong></summary>

- Create cgroup dirs in `/sys/fs/cgroup`  
- Apply CPU quota + memory limit  
- Confirm with stress tests

</details>

<details>
<summary><strong>Module 35: Implement Networking</strong></summary>

- Create veth pair (host ↔ container)  
- Move one end to container ns  
- Attach host end to Linux bridge  
- Assign IPs, verify ping + comms

</details>

<details>
<summary><strong>Module 36: Env Vars & Command Args</strong></summary>

- Pass env vars via CLI  
- Pass command args to child

</details>

<details>
<summary><strong>Module 37: Pre-loading a Root Filesystem</strong></summary>

- Preload rootfs for faster spins

</details>

<details>
<summary><strong>Module 38: Minimal Dockerfile Runner</strong></summary>

- Support: `FROM`, `COPY`, `CMD`  
- Simple image loader

</details>

<details>
<summary><strong>Module 39: Final CLI — mydocker run</strong></summary>

- Final runnable CLI with all features

</details>

---

## Milestone 5: CNI & Container Networking (Bridge + Overlay) in Go

<details>
<summary><strong>Module 40: CNI Plugin Bootstrap</strong></summary>

- Understand CNI spec (ADD, DEL, CHECK)  
- Plugin folder structure  
- Parse CNI stdin JSON  
- Print result JSON

</details>

<details>
<summary><strong>Module 41: Implement Basic IPAM</strong></summary>

- IP allocation/release  
- Integrate into CNI lifecycle

</details>

<details>
<summary><strong>Module 42: Create veth Pair & Attach to Bridge</strong></summary>

- Create veth `cni0 ↔ <container>`  
- Move veth to container ns  
- Create Linux bridge `cni0`  
- Assign gateway IP  
- Test container ↔ host ↔ gateway

</details>

<details>
<summary><strong>Module 43: Configure Routes & Enable Egress</strong></summary>

- Add default route inside ns  
- Setup NAT/MASQUERADE  
- Enable IP forwarding

</details>

<details>
<summary><strong>Module 44: Build CNICtl Debug CLI</strong></summary>

- Create CLI tools for inspecting / debugging CNI

</details>

<details>
<summary><strong>Module 45: Multi-Node Networking Foundations</strong></summary>

- VXLAN basics (VNI, FDB, neighbors)  
- Create VXLAN interface manually

</details>

<details>
<summary><strong>Module 46: Add VXLAN Overlay Support</strong></summary>

- Create VXLAN link  
- Add remote nodes  
- Assign overlay IPs  
- Route pod IPs via VXLAN

</details>

<details>
<summary><strong>Module 47: Add Distributed IPAM</strong></summary>

- Central IPAM via file/Redis/HTTP  
- Concurrency-safe allocate/release

</details>

<details>
<summary><strong>Module 48: Integrate with Docker Runtime</strong></summary>

- mydocker calls CNI plugin  
- Config: `/etc/cni/net.d/container-net.conf`

</details>

<details>
<summary><strong>Module 49: Final Demo — Pod Networking Simulation</strong></summary>

- End-to-end demo of pod networking

</details>

---

## Milestone 6: gRPC + Mini Go Web Framework

<details>
<summary><strong>Module 50: gRPC Setup & Protobuf Basics</strong></summary>

- Install protoc + Go plugins  
- First `.proto`  
- Generate Go code  
- Server + client

</details>

<details>
<summary><strong>Module 51: Unary RPC Service</strong></summary>

- `SayHello` method  
- Request/response types  
- Logging interceptor

</details>

<details>
<summary><strong>Module 52: Server-Side Streaming</strong></summary>

- Stream `ListUsers`  
- Consume via client loop

</details>

<details>
<summary><strong>Module 53: Client-Side & Bi-Directional Streaming</strong></summary>

- Client streaming uploads  
- Bidi chat RPC  
- Stream contexts

</details>

<details>
<summary><strong>Module 54: Interceptors & Middleware</strong></summary>

- Unary & stream interceptors  
- Logging  
- Auth token validation  
- Error translation

</details>

<details>
<summary><strong>Module 55: gRPC with TLS</strong></summary>

- Generate certs  
- Enable secure channels

</details>

<details>
<summary><strong>Module 56: gRPC Gateway (REST + gRPC)</strong></summary>

- Add HTTP endpoints  
- Serve JSON + protobuf

</details>

<details>
<summary><strong>Module 57: Load Balancing + Health Checks</strong></summary>

- Custom LB client  
- Health check service  
- Retries/timeouts

</details>

<details>
<summary><strong>Module 58: Build a Basic Router (Mini HTTP Framework)</strong></summary>

- Method+path → handler routing  
- Path params (`/user/:id`)  
- Context struct

</details>

<details>
<summary><strong>Module 59: Middleware Pipeline</strong></summary>

- Logging middleware  
- Recovery middleware  
- CORS (optional)

</details>

<details>
<summary><strong>Module 60: JSON Helpers & Validation</strong></summary>

- `ctx.JSON()`  
- `ctx.Bind()`  
- Request validation

</details>

<details>
<summary><strong>Module 61: Grouped Routes + Modular Design</strong></summary>

- `/api/v1` grouping  
- Nested groups  
- Clean folders

</details>

<details>
<summary><strong>Module 62: Build REST App Using Framework</strong></summary>

- CRUD handlers  
- Middleware usage  
- Auth (JWT/static token)

</details>

---

## Milestone 7: Temporal & Reliable Payment Workflow in Go

<details>
<summary><strong>Module 63: First Workflow & Activity</strong></summary>

- Setup Temporal local server  
- Web UI  
- HelloWorkflow  
- First Activity

</details>

<details>
<summary><strong>Module 64: Workflow State & Signals</strong></summary>

- Internal state  
- Signals  
- Queries  
- Replay behavior

</details>

<details>
<summary><strong>Module 65: Activity Retries & Errors</strong></summary>

- Retry policies  
- Timeout handling  
- Failure simulation

</details>

<details>
<summary><strong>Module 66: Timers, Sleep, Cron</strong></summary>

- `workflow.Sleep()`  
- Order-expiration timer  
- Cron workflows

</details>

---

## Milestone 8: Multi-Tenant Orchestrator in Go

<details>
<summary><strong>Module 67: Architecture Setup</strong></summary>

- Components (API, Scheduler, Worker)  
- State store (Redis/Postgres)  
- Job + Tenant models

</details>

<details>
<summary><strong>Module 68: Build API Server</strong></summary>

- POST `/tenants`  
- POST `/jobs`  
- GET `/jobs/:id`  
- GET `/tenants/:id/usage`

</details>

<details>
<summary><strong>Module 69: Implement State Store</strong></summary>

- Jobs lifecycle storage  
- Tenant quotas  
- Worker heartbeats  
- TTL for dead jobs

</details>

<details>
<summary><strong>Module 70: Worker Agent Basics</strong></summary>

- Register + heartbeat  
- Fetch jobs  
- Run containers  
- Report status

</details>

<details>
<summary><strong>Module 71: Scheduling Queue & Isolation</strong></summary>

- Pending queue  
- Per-tenant concurrency limits  
- CPU/memory budget  
- Rate limiting

</details>

<details>
<summary><strong>Module 72: Resource-Based Scheduling</strong></summary>

- Resource request model  
- Worker capacity model  
- Capacity-aware scheduling

</details>

<details>
<summary><strong>Module 73: Execution Engine & Logging</strong></summary>

- Run jobs as containers  
- Capture stdout/stderr

</details>

<details>
<summary><strong>Module 74: Multi-Tenant Observability</strong></summary>

- Running/failed jobs  
- Usage summary  
- Throttle history

</details>

---

## Milestone 9: Kubernetes Core Internals

<details>
<summary><strong>Module 75: Kubernetes Architecture Overview</strong></summary>

- API Server, etcd  
- Controllers, Scheduler  
- Kubelet  
- CRI/CNI/CSI

</details>

<details>
<summary><strong>Module 76: etcd Basics & Pod Anatomy</strong></summary>

- Install etcd  
- KV ops + watches  
- `etcdctl` inspection  
- Pod YAML + objects

</details>

<details>
<summary><strong>Module 77: Workloads & Controller Pattern</strong></summary>

- Deployments, ReplicaSets  
- Reconciliation loops  
- Scaling + watching Pods

</details>

<details>
<summary><strong>Module 78: RBAC Concepts</strong></summary>

- ServiceAccount  
- Role/RoleBinding  
- Permission model

</details>

<details>
<summary><strong>Module 79: Kubernetes Networking</strong></summary>

- Pod network model  
- Service types  
- DNS/CoreDNS

</details>

<details>
<summary><strong>Module 80: Kubelet & Scheduler</strong></summary>

- Node status  
- Pod lifecycle events  
- CRI/CNI interactions

</details>

---

## Milestone 10: Kubernetes Controller Development

<details>
<summary><strong>Module 81: Controller Development (Kubebuilder)</strong></summary>

- CRDs & API extensions  
- Controller runtime + reconciliation  
- Finalizers, garbage collection  
- Leader election & HA controllers  
- Admission webhooks  
- Watches, informers, caching  
- Testing (unit/E2E)  
- Performance & scaling  
- Security & RBAC  
- External integrations (Cloud/GitOps/Vault)  
- Packaging/versioning (Helm)  
- Production case studies

</details>

---

## Milestone 11: AWS for Go Engineer

<details>
<summary><strong>Module 82: AWS Networking</strong></summary>

- EC2 in VPC  
- Bastion in public subnet  
- Secure VPC design  
- Bastion → private SSH

</details>

<details>
<summary><strong>Module 83: AWS Compute</strong></summary>

- Go REST API on EC2  
- systemd deployment  
- Go + MySQL private subnet  
- Go + MongoDB stack  
- Go + Redis systemd  
- Nginx L4 load balancer  
- GitHub Actions deployment

</details>

<details>
<summary><strong>Module 84: AWS to Build Systems</strong></summary>

- FastAPI + Docker Compose  
- Deploy from DockerHub  
- Build/push to ECR  
- REST API (FastAPI + SQLAlchemy + MySQL)  
- MySQL migrations  
- MongoDB Motor async  
- GraphQL with FastAPI

</details>

---

## Milestone 12: Build Mini Kubernetes

<details>
<summary><strong>Module 85: Mini-K8s API Server Skeleton</strong></summary>

- HTTP/gRPC API server  
- CRUD Pods/Nodes/Deployments  
- etcd/BoltDB state  
- Watch streams

</details>

<details>
<summary><strong>Module 86: Build Node Agent</strong></summary>

- Node registration  
- Heartbeats  
- Monitor local Pods

</details>

<details>
<summary><strong>Module 87: Pod Sandbox & Launching</strong></summary>

- Run containers  
- Namespaces + mounts  
- Configure CNI  
- Report status

</details>

<details>
<summary><strong>Module 88: Scheduler & Resource Tracking</strong></summary>

- Watch unscheduled Pods  
- Filter/score nodes  
- Bind Pods  
- Track CPU/memory

</details>

<details>
<summary><strong>Module 89: ReplicaSet & Node Controller</strong></summary>

- Ensure desired replicas  
- Self-healing  
- Detect dead nodes  
- Evict + reschedule

</details>

<details>
<summary><strong>Module 90: Pod Lifecycle Controller</strong></summary>

- Pending → Running → Succeeded/Failed  
- Cleanup + restart policies

</details>

<details>
<summary><strong>Module 91: Integrate CNI Plugin</strong></summary>

- Call your CNI  
- Assign IPs + veth/overlay  
- Validate pod-to-pod

</details>

<details>
<summary><strong>Module 92: Implement ClusterIP Service</strong></summary>

- Service registry  
- Random LB  
- Validate routing

</details>

<details>
<summary><strong>Module 93: Multi-Node Deployment</strong></summary>

- 1 API server  
- 1 Scheduler  
- 1 Controller manager  
- 2 Node agents  
- Run sample manifests

</details>

<details>
<summary><strong>Module 94: Failure Simulation</strong></summary>

- Kill node agent → reschedule  
- Restart API server → recover etcd

</details>

<details>
<summary><strong>Module 95: YAML Manifest Loader</strong></summary>

- Parse Pod/Deployment YAML  
- Apply to API server

</details>

<details>
<summary><strong>Module 96: Metrics Endpoint</strong></summary>

- Cluster metrics  
- Pod count, readiness, latency

</details>
