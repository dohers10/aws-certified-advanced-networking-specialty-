## General
    - Dockerfile - used to build docker images, goes through step by step
    - Portable, self contained - always run as expected
    - all images are created from base imagine or scratch
    - Container registry; where container images are stored( docker files)

## DEMO
-> Deploy proided CFN, deploys EC2 pre-installed.
# Install Docker Engine on EC2 Instance
sudo amazon-linux-extras install docker
sudo service docker start
sudo usermod -a -G docker ec2-user

LOGOUT and login

sudo su - ec2-user

# Build Docker Image
cd container
docker build -t containerofcats .
docker images --filter reference=containerofcats

# Run Container from Image
docker run -t -i -p 80:80 containerofcats

# Upload Container to Dockerhub (optional)
docker login --username=YOUR_USER
docker images
docker tag IMAGEID YOUR_USER/containerofcats
docker push YOUR_USER/containerofcats:latest