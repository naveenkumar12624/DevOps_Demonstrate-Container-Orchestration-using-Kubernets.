# Experiment 06: Demonstrate-Container-Orchestration-using-Kubernets

<h2>Aim</h2>
<p>The aim of this experiment is to introduce students to container orchestration using Kubernetes and demonstrate how to deploy a containerized web application. By the end of this experiment, students will have a basic understanding of Kubernetes concepts and how to use Kubernetes to manage containers.</p>

<h2>Theory</h2>
<p>Container orchestration is a critical component in modern application deployment, allowing you to manage, scale, and maintain containerized applications efficiently. Kubernetes is a popular container orchestration platform that automates many tasks associated with deploying, scaling, and managing containerized applications. This experiment will demonstrate basic container orchestration using Kubernetes by deploying a simple web application.</p>

<h3>Key Concepts in Kubernetes</h3>
<ul>
  <li><strong>Containerization:</strong> Kubernetes relies on containers as the fundamental unit for packaging and running applications.</li>
  <li><strong>Cluster:</strong> A set of machines that collectively run containerized applications, consisting of master and worker nodes.</li>
  <li><strong>Nodes:</strong> Machines that form part of a Kubernetes cluster and run containerized workloads.</li>
  <li><strong>Pod:</strong> The smallest deployable unit in Kubernetes.</li>
  <li><strong>Deployment:</strong> Defines how to create, update, and scale application instances.</li>
  <li><strong>Service:</strong> Exposes a set of pods as a network service.</li>
  <li><strong>Namespace:</strong> Provides resource isolation within a cluster.</li>
</ul>

<h3>Key Features of Kubernetes</h3>
<ul>
  <li>Automated Scaling</li>
  <li>Load Balancing</li>
  <li>Self-healing</li>
  <li>Rolling Updates and Rollbacks</li>
  <li>Storage Orchestration</li>
  <li>Configuration Management</li>
  <li>Extensibility</li>
</ul>

<h2>Materials</h2>
<ul>
  <li>A computer with Kubernetes installed (<a href="https://kubernetes.io/docs/setup/" target="_blank">Install Kubernetes</a>)</li>
  <li>Docker installed (<a href="https://docs.docker.com/get-docker/" target="_blank">Install Docker</a>)</li>
</ul>

<h2>Experiment Steps</h2>

<h3>Step 1: Create a Dockerized Web Application</h3>
<ul>
  <li>Create a simple web application or use an existing one.</li>
  <li>Create a Dockerfile to package the web application into a Docker container:</li>
</ul>
<pre><code># Use an official Nginx base image
FROM nginx:latest
# Copy the web application files to the Nginx document root
COPY ./webapp /usr/share/nginx/html
</code></pre>
<ul>
  <li>Build the Docker image:</li>
</ul>
<pre><code>docker build -t my-web-app .</code></pre>

<h3>Step 2: Deploy the Web Application with Kubernetes</h3>
<p>Create a Kubernetes Deployment YAML file (<code>web-app-deployment.yaml</code>):</p>
<pre><code>apiVersion: apps/v1
kind: Deployment
metadata:
name: my-web-app-deployment
spec:
replicas: 3
selector:
matchLabels:
app: my-web-app
template:
metadata:
labels:
  app: my-web-app
spec:
containers:
- name: my-web-app-container
  image: my-web-app:latest
  ports:
  - containerPort: 80
</code></pre>

<h3>Step 3: Deploy the Application</h3>
<ul>
  <li>Apply the deployment configuration:</li>
</ul>
<pre><code>kubectl apply -f web-app-deployment.yaml</code></pre>

<h3>Step 4: Verify the Deployment</h3>
<ul>
  <li>Check the status of your pods:</li>
</ul>
<pre><code>kubectl get pods</code></pre>

<h2>Conclusion</h2>
<p>In this experiment, you learned how to create a Kubernetes Deployment for container orchestration. The <code>web-app-deployment.yaml</code> file defines the desired state of the application, including the number of replicas, labels, and the Docker image to use. Kubernetes automates the deployment and scaling of the application, making it a powerful tool for managing containerized workloads.</p>


