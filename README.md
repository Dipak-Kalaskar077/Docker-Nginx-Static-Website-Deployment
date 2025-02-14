# Docker Nginx Deployment with Free CSS Template

## Overview
This project demonstrates how to deploy an Nginx server inside a Docker container and host a free CSS template on it. This setup is ideal for quickly deploying static websites with Docker.

---

## Prerequisites
Before you begin, ensure you have the following installed:
- **Docker** installed on your system
- **Basic Linux command-line knowledge**
- **An AWS EC2 instance (if deploying on AWS)**

---

## Installation Steps

### Step 1: Install Docker
Update your system and install Docker:
```bash
sudo apt-get update && sudo apt-get install docker.io -y
```
Verify the installation:
```bash
docker --version
```

### Step 2: Run an Nginx Container
Create and run an Nginx container, exposing it on port 8080:
```bash
docker run -d --name my-nginx -p 8080:80 nginx
```
Verify the container is running:
```bash
docker ps
```

### Step 3: Download a Free CSS Template
Find a free CSS template from [Free CSS](https://www.free-css.com) and copy the download URL. Then, run:
```bash
wget -O template.zip https://www.free-css.com/assets/files/free-css-templates/download/page296/Filename.zip
```
(Replace `Filename.zip` with the actual file name.)

### Step 4: Extract Template Files
Create a directory and extract the template:
```bash
mkdir finexo-html && cd finexo-html
apt-get install unzip -y
unzip ../template.zip -d .
```
Verify the extracted files:
```bash
ls
```

### Step 5: Copy Files into the Nginx Container
Find your container ID:
```bash
docker ps
```
Copy the files to the container:
```bash
docker cp finexo-html/. <container_id>:/usr/share/nginx/html/
```
Replace `<container_id>` with your actual container ID.

### Step 6: Verify the Deployment
Restart the Nginx container:
```bash
docker restart my-nginx
```
Now, open your browser and go to:
```
http://localhost:8080
```

---

## Deploying on AWS EC2
If deploying on AWS, update the security group:
1. Go to **AWS Console → EC2 → Security Groups**
2. Edit **Inbound Rules** and add:
   - **Rule 1:** HTTP, TCP, Port: `80`, Source: `0.0.0.0/0`
   - **Rule 2:** Custom TCP, TCP, Port: `8080`, Source: `0.0.0.0/0`
3. Open your EC2 Public IP in the browser:
   ```
   http://<your-ec2-public-ip>:8080
   ```

---

## Troubleshooting
- Restart the container:
  ```bash
  docker restart my-nginx
  ```
- Check Nginx logs:
  ```bash
  docker logs my-nginx
  ```
- Ensure the security group allows traffic on ports 80 and 8080.

---

## Conclusion
Congratulations! 🎉 You have successfully deployed an Nginx container with a free CSS template using Docker. This method allows for quick static site hosting and can be extended with SSL, reverse proxy, and backend integration.

### 💡 Found this helpful? Give this repo a ⭐ and share it!

---

## License
This project is licensed under the MIT License.

## Author
LinkedIn (https://linkedin.com/in/dipak-kalaskar)

---

