---

# **Fun with Docker! 🚢🐳**
## **Exercise 1: Getting Started with Docker**

Let’s start with some hands-on Docker magic! ✨ Follow these steps to explore the basics.

1. **Check if Docker is Installed:**  
   Open your terminal and type:  
   ```bash
   docker --version
   ```  
   If Docker is installed, you’ll see the version number. 🎉

2. **Run Your First Docker Container!** 🐳  
   Type this command to pull and run a basic test container:  
   ```bash
   docker run hello-world
   ```  
   If all goes well, you should see a friendly message!

3. **Download an Ubuntu Image:**  
   ```bash
   docker pull ubuntu
   ```  
   Now, check your downloaded images:  
   ```bash
   docker images
   ```  

4. **Launch an Ubuntu Container (Interactive Mode):**  
   ```bash
   docker run -it ubuntu /bin/bash
   ```  
   You’re now inside a running Ubuntu container! Type `exit` to leave.

5. **Pull and Run an Apache Web Server:** 🌐  
   ```bash
   docker pull httpd
   docker run -d -p 80:80 --name my-apache-server httpd
   ```  
   Open your browser and visit [http://localhost](http://localhost). You should see Apache running!

6. **See All Running Containers:**  
   ```bash
   docker ps
   ```

7. **Stop the Apache Web Server:**  
   ```bash
   docker stop my-apache-server
   ```

8. **View All Stopped Containers:**  
   ```bash
   docker ps -a
   ```

9. **Remove a Container:** 🗑️  
   ```bash
   docker rm my-apache-server
   ```

10. **Run an Nginx Web Server:**  
    ```bash
    docker run --name my-web-server -d -p 80:80 nginx
    ```  
    Check if it’s running:  
    ```bash
    docker ps
    ```

---

## **Exercise 2: Networking with Docker** 🌍

1. **Create a Custom Network:**  
   ```bash
   docker network create my-network
   ```

2. **View All Networks:**  
   ```bash
   docker network ls
   ```

3. **Connect Your Web Server to the Network:**  
   ```bash
   docker network connect my-network my-web-server
   ```

4. **Check if It’s Connected:**  
   ```bash
   docker inspect my-web-server
   ```

5. **See Which Containers Are on the Network:**  
   ```bash
   docker network inspect my-network
   ```

---

## **Exercise 3: Storing Data with Docker Volumes** 💾

1. **Create a Docker Volume:**  
   ```bash
   docker volume create my-volume
   ```

2. **Attach the Volume to Your Web Server:**  
   - Stop and remove the existing container:  
     ```bash
     docker stop my-web-server
     docker rm my-web-server
     ```
   - Re-run the container with the volume attached:  
     ```bash
     docker run --name my-web-server -d -p 80:80 -v my-volume:/usr/share/nginx/html nginx
     ```

3. **Update the Web Page Content:**  
   - Access the container:  
     ```bash
     docker exec -it my-web-server /bin/bash
     ```
   - Change the default message:  
     ```bash
     echo "Hello, world!" > /usr/share/nginx/html/index.html
     ```
   - Exit and refresh [http://localhost](http://localhost) to see your change!

---

## **Exercise 4: Build Your Own Docker Image! 🏗️**

1. **Clone the Exercise Repository:**  
   ```bash
   git clone https://github.com/damianigbe/docker-exercises.git
   cd docker-exercises/exercise-1
   ```

2. **Build Your Custom Docker Image:**  
   ```bash
   docker build -t myimage .
   ```

3. **Run a Container from Your Image:**  
   ```bash
   docker run -d --name mycontainer -p 80:80 myimage
   ```

4. **Access Your Web App:**  
   Open a browser and go to:  
   - [http://127.0.0.1/docs](http://127.0.0.1/docs)  
   - or [http://localhost/docs](http://localhost/docs)

---

## **Exercise 5: Share Your Work on Docker Hub! 🚀**

1. **Sign Up for Docker Hub** (if you haven’t already):  
   [Sign up here!](https://hub.docker.com/)

2. **Log in to Docker from the Terminal:**  
   ```bash
   docker login
   ```

3. **Tag Your Image for Upload:**  
   ```bash
   docker tag myimage username/myimage
   ```

4. **Push the Image to Docker Hub:**  
   ```bash
   docker push username/myimage
   ```

5. **Verify It’s Online:**  
   Check your Docker Hub account to see your uploaded image!

---

## **Exercise 6: Build a Microservice with Flask & Docker** 🏗️📚

1. **Navigate to the Flask App Directory:**  
   ```bash
   cd rest-api-microservice-docker/
   ```

2. **Build the Docker Image:**  
   ```bash
   docker build -t flaskbookapi:1.0 .
   ```

3. **Run the Flask App Container:**  
   ```bash
   docker run -p 5000:5000 --name FlaskBookAPI flaskbookapi:1.0
   ```

4. **Test Your API:**  
   - In a browser: [http://localhost:5000/books](http://localhost:5000/books)  
   - Or using `curl`:  
     ```bash
     curl localhost:5000/books
     ```

---

## **Bonus Challenge: Complete These Before the Next Class! 🏆**

### **1. Upload Your Flask API Image to Docker Hub**
- Tag and push your `flaskbookapi:1.0` image to Docker Hub.

### **2. Deploy a Static Website**
- Navigate to the `static-site` folder from Exercise 2.
- Build a Docker image for it.
- Tag and push it to Docker Hub.
- Run the container and access your website.

🎉 **Congratulations! You’re now comfortable using Docker!** 🚢🔥
