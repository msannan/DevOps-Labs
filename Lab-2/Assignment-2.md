# Assignment 2

# Explain Docker Containers vs VMs
  Containers: A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.
  VM's: A virtual machine (VM) is a virtual environment that functions as a virtual computer system with its own CPU, memory, network interface, and storage, created on a physical hardware system (located off- or on-premises). Software called a hypervisor separates the machine’s resources from the hardware and provisions them appropriately so they can be used by the VM. 
  
  Comparion: (Docker vs VMs)
  OS Level Virtualization  vs Hardware level virtualization 
  Efficient Resource Utilization vs 10s GB of utilization (seperate OS, memory, cpu)
  Less isolation vs more isloated compared to dockers
  Run anywhere vs need seperate environment
  Quickly scalable, lightweight vs difficult to scale

# Explain Docker Architecture
  - Docker Client: A simple CLI to interact with docker deamon
  - Docker Deamon: is the main component running on OS and communicating with OS. Deamon is responsible to create, run, delete and monitor containers
  - Docker registry: is a repository where docker images are stored
# Write command to create an nginx container in detached mode with name assignment-2 running on host port 9090 on a custom network named assignment-2
  `docker container run -d --name assignment-2 -p 9090:80 --net assignment-2 nginx`

# Write command to see logs of the above container
  `docker container logs assignment-2`

# Write commands to Exec into the container and cat the output of the default nginx file at /usr/share/nginx/html/index.html 
  `docker container exec -it assignment-2 cat /usr/share/nginx/html/index.html`
# Exit the above container, and now recreate the container by Volume using bind mounting
  `docker container run -d --name assignment-2 -p 9090:80 --net assignment-2 -v /Users/sannan/data:/usr/share/nginx/html nginx`
# Command to exec into the above container and replace the default index.html to a custom one, which says that â€œI am becoming a Docker Expertâ€ and it should be persisted for the next times.
  `echo "<html\><head><title>Learn Docker</title></head><body><h1>I am becomming a docker expert</h1></body></html>" > /tmp/index.html`
  
  `docker cp index.html assignment-2:/usr/share/nginx/html/index.html`
