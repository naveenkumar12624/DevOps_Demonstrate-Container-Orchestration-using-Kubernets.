# Experiment 4 : DevOps_Demonstrate-Container-Orchestration-using-Kubernets


<h1>Aim</h1>
<p>
The objective of this experiment is to provide hands-on experience with Docker containerization 
and application deployment by deploying an Apache web server in a Docker container. 
By the end of this experiment, you will understand the basics of Docker, how to create Docker containers, 
and how to deploy a simple web server application.
</p>

<h1>Theory</h1>
<p>
Containerization is a technology that has revolutionized the way applications are developed, deployed, 
and managed in the modern IT landscape. It provides a standardized and efficient way to package, 
distribute, and run software applications and their dependencies in isolated environments called containers.
</p>
<p>
Containerization technology has gained immense popularity, with Docker being one of the most well-known 
containerization platforms. This introduction explores the fundamental concepts of containerization, 
its benefits, and how it differs from traditional approaches to application deployment.
</p>

<h2>Key Concepts of Containerization</h2>
<ul>
<li>
  <b>Containers:</b> Containers are lightweight, stand-alone executable packages that include everything 
  needed to run a piece of software, including the code, runtime, system tools, libraries, and settings. 
  Containers ensure that an application runs consistently and reliably across different environments, 
  from a developer's laptop to a production server.
</li>
<li>
  <b>Images:</b> Container images are the templates for creating containers. They are read-only and contain 
  all the necessary files and configurations to run an application. Images are typically built from a set 
  of instructions defined in a Dockerfile.
</li>
<li>
  <b>Docker:</b> Docker is a popular containerization platform that simplifies the creation, distribution, 
  and management of containers. It provides tools and services for building, running, and orchestrating 
  containers at scale.
</li>
<li>
  <b>Isolation:</b> Containers provide process and filesystem isolation, ensuring that applications and 
  their dependencies do not interfere with each other. This isolation enhances security and allows 
  multiple containers to run on the same host without conflicts.
</li>
</ul>

<h2>Benefits of Containerization</h2>
<ul>
<li>Consistency: Containers ensure that applications run consistently across different environments, reducing the "it works on my machine" problem.</li>
<li>Portability: Containers are portable and can be easily moved between different host machines and cloud providers.</li>
<li>Resource Efficiency: Containers share the host operating system's kernel, which makes them lightweight and efficient in terms of resource utilization.</li>
<li>Scalability: Containers can be quickly scaled up or down to meet changing application demands, making them ideal for microservices architectures.</li>
<li>Version Control: Container images are versioned, enabling easy rollback to previous application states if issues arise.</li>
<li>DevOps and CI/CD: Containerization is a fundamental technology in DevOps and CI/CD pipelines, allowing for automated testing, integration, and deployment.</li>
</ul>

<h2>Containerization vs. Virtualization</h2>
<p>
Containerization differs from traditional virtualization, where a hypervisor virtualizes an entire operating 
system (VM) to run multiple applications. In contrast:
</p>
<ul>
<li>Containers share the host OS kernel, making them more lightweight and efficient.</li>
<li>Containers start faster and use fewer resources than VMs.</li>
<li>VMs encapsulate an entire OS, while containers package only the application and its dependencies.</li>
</ul>

<h1>Materials</h1>
<ul>
<li>A computer with Docker installed (<a href="https://docs.docker.com/get-docker/">https://docs.docker.com/get-docker/</a>)</li>
<li>A code editor</li>
<li>Basic knowledge of Apache web server</li>
</ul>

<h1>Experiment Steps</h1>
<h2>Step 1: Install Docker</h2>
<ul>
<li>If you haven't already, install Docker on your computer by following the instructions provided on the <a href="https://docs.docker.com/get-docker/">Docker website</a>.</li>
</ul>

<h2>Step 2: Create a Simple HTML Page</h2>
<ul>
<li>Create a directory for your web server project.</li>
<li>Inside this directory, create a file named <code>index.html</code> with a simple "Hello, Docker!" message. This will be the content served by your Apache web server.</li>
</ul>

<h2>Step 3: Create a Dockerfile</h2>
<ul>
<li>Create a <code>Dockerfile</code> in the same directory as your web server project. The <code>Dockerfile</code> defines how your Apache web server application will be packaged into a Docker container. Here's an example:</li>
</ul>
<pre>
<code>
# Use an official Apache image as the base image
FROM httpd:2.4

#Copy your custom HTML page to the web server's document root******
COPY index.html /usr/local/apache2/htdocs/
</code>
</pre>

<h2>Step 4: Build the Docker Image</h2>
<ul>
<li>Build the Docker image by running the following command in the same directory as your <code>Dockerfile</code>:</li>
</ul>
<pre>
<code>
docker build -t my-apache-server .
</code>
</pre>
<ul>
<li>Replace <code>my-apache-server</code> with a suitable name for your image.</li>
</ul>

<h2>Step 5: Run the Docker Container</h2>
<pre>
<code>
docker run -p 8080:80 -d my-apache-server
</code>
</pre>
<ul>
<li>This command maps port 80 in the container to port 8080 on your host machine and runs the container in detached mode.</li>
</ul>

<h2>Step 6: Access Your Apache Web Server</h2>
<ul>
<li>Access your Apache web server by opening a web browser and navigating to:</li>
</ul>
<pre>
<code>http://localhost:8080</code>
</pre>

<h2>Step 7: Cleanup</h2>
<ul>
<li>Stop the running Docker container:</li>
</ul>
<pre>
<code>
docker stop &lt;container_id&gt;
</code>
</pre>
<ul>
<li>Replace <code>&lt;container_id&gt;</code> with the actual ID of your running container.</li>
<li>Optionally, remove the container and the Docker image:</li>
</ul>
<pre>
<code>
docker rm &lt;container_id&gt;
docker rmi my-apache-server
</code>
</pre>

<h1>Conclusion</h1>
<p>
In this experiment, you explored containerization and application deployment with Docker by deploying an Apache web server in a Docker container. 
You learned how to create a Dockerfile, build a Docker image, run a Docker container, and access your web server application from your host machine. 
Docker's containerization capabilities make it a valuable tool for packaging and deploying applications consistently across different environments.
</p>

