1.Setup EC2 Instance:
Launched an Ubuntu EC2 instance and installed Jenkins and Docker.

2.Created Simple Web App:
Built a simple index.html page and placed it in a project folder /root/simple-web-app.

3.Dockerized the App:
Created a Dockerfile using Nginx to serve the HTML page.

4.Created Jenkins Pipeline:
Added a Jenkinsfile with 3 stages: Build, Test, and Deploy.
Build: Builds the Docker image
Test: Verifies the image by running a temporary container
Deploy: Runs the final container on port 8081.

5.Configured Jenkins Pipeline:
Created a pipeline job in Jenkins pointing to the GitHub repo.
Triggered the pipeline → Jenkins automatically built, tested, and deployed the container.

6.Verified Deployment:
Opened http://ec2-Public-IP:8081 in the browser → HTML page displayed successfully.
