# My path to know how to use Docker

**Docker** is a tool that lets us package an application together with everything it needs to run—code, dependencies, libraries, and configuration.  
This allows the application to run the same way in any environment, ensuring consistency, portability, and avoiding “it works on my machine” problems.

### Why we should use Docker

1. **Consistency across environments**  
    Docker ensures that an application runs the same way in development, testing, and production. Since the app and all its dependencies are packaged together, there are no surprises caused by differences in operating systems, library versions, or configurations. This solves the common “it works on my machine” problem.
    
2. **Portability**  
    A Docker container can run on any system that has Docker installed, whether it’s a developer’s laptop, a company server, or a cloud platform. This makes applications highly portable and easy to move between environments without modification.
    
3. **Simplified setup and dependency management**  
    With Docker, there is no need to manually install and configure dependencies on each machine. Everything the application needs is defined in a Dockerfile and built into the image. This reduces setup time and minimizes human error.
    
4. **Isolation of applications**  
    Each Docker container runs in isolation, meaning applications do not interfere with one another. Different projects can use different versions of the same dependency on the same machine without conflict.
    
5. **Faster development and on boarding**  
    New developers can get started quickly by running a single command to start the application, instead of spending hours configuring their environment. This improves productivity and collaboration within teams.
    
6. **Efficient resource usage**  
    Docker containers are lightweight compared to virtual machines because they share the host system’s kernel. This allows multiple containers to run efficiently on the same system with minimal overhead.
    
7. **Easier deployment and scalability**  
    Docker makes it easier to deploy applications consistently and repeatedly. Containers can be scaled up or down quickly, which is especially useful for modern architectures like micro-services and cloud-based systems.

### How Docker works
Docker works by using a Dockerfile to define how an application and its environment should be built. Docker then creates an image from this file, which serves as a read-only blueprint. When the image is run, Docker creates instances, known as **containers**, from a Docker image. Multiple containers can be created from the same image, while sharing the same underlying configuration. Each container runs in isolation but shares the **host machine’s operating system kernel and system resources**, making containers lightweight, fast, and efficient compared to virtual machines.
#### **Docker volumes** 
are used to keep data safe when containers are stopped or removed. Containers are temporary by nature, so any data stored inside them is lost when they are deleted. A volume allows Docker to store this data outside the container on the host machine while still making it accessible from inside the container. This means applications like databases or apps that save files can keep their data even if the container is restarted or recreated. Volumes help separate application code from data and are essential for real-world Docker usage. they can be **shared between multiple containers**, allowing them to access the same files and data. For example, two containers could read and write to the same database files or share uploaded files. This works because the volume exists **outside the containers** on the host machine, so any container that mounts it sees the same data.

#### **Docker network**
Docker containers are isolated by default, so they can’t communicate with each other unless connected through a **Docker network**. A network allows containers to safely send messages and share services, similar to a restaurant kitchen where each station (container) has a chef (process) specializing in a particular task, like grilling, making salads, or preparing desserts. Even though each chef works independently, they can communicate with each other over the kitchen’s communication system (the network) and share ingredients from the pantry (volumes) when needed. This way, containers can work together efficiently while still being isolated, just like a well-coordinated kitchen.

### Docker workflow

1. **Docker Client**
	The **Docker client** is like the **restaurant manager** who gives orders to the kitchen. It’s the tool you use to tell Docker what to do, like “build this dish” or “start this station.” You interact with it by typing commands such as `docker build` or `docker run`. The client doesn’t cook anything itself — it just sends instructions to the Docker daemon (the chefs) to do the work.
2. **Docker Daemon**
	The **Docker daemon** is like the **team of chefs in the kitchen**. It actually does all the work: building the dishes (images), running the cooking stations (containers), and managing ingredients (volumes) and communication between stations (networks). When the manager (client) gives an order, the daemon carries it out behind the scenes. Without the daemon, the commands from the client wouldn’t be executed.
3. **Docker Registry**
	The **Docker registry** is like the **pantry or recipe book** in the restaurant. It stores all the ready-made dishes (Docker images) that the chefs can use. For example, if the restaurant wants a classic burger, the chefs can pull the recipe and ingredients from the pantry instead of making it from scratch. Docker Hub is the default registry, but restaurants (companies) can have their own private pantries too. When you run `docker pull ubuntu`, it’s like asking the pantry for a pre-made dish so the chefs can start cooking immediately.
 