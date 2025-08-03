# MultienvApp 

🧩 2. Directory & File Structure 
cloud_container/
│
├── backend-dev/
│   ├── Dockerfile
│   └── .env
│
├── backend-prod/
│   ├── Dockerfile
│   └── .env
│
├── frontend/
│   ├── Dockerfile
│   └── .env
│
├── docker-compose.yml
├── README.md


****---------------------------------------------****
⚙️ 3.  docker-compose.yml 

version: "3"

services:
  backend-dev:
    build:
      context: ./backend/dev 
    ports:
      - "5000:5000" 
    env_file:
      - ./backend/dev/.env 

  backend-prod:
    build:
      context: ./backend/prod 
    ports:
      - "5001:5001" 
    env_file:
      - ./backend/prod/.env 

  frontend: 
    build:
      context: ./frontend 
    ports: 
      - "3000:3000"  
    env_file:
      - ./frontend/.env  

  ****--------------------------------------------****

🔧 EC2 Instance Setup Steps
1. Launch EC2 Instance
Go to AWS Console

Navigate to EC2 Dashboard → Click Launch Instance

Configure:

Name: multi-env-deployment

AMI: Ubuntu Server 22.04 LTS (recommended)

Instance Type: t2.micro (Free tier eligible)

Key Pair: Create new or use existing key (download .pem file)

Storage: Default 8 GiB (increase if needed)

Security Group:

Add Inbound Rules:

Type: HTTP | Port: 80 | Source: Anywhere

Type: Custom TCP | Port: 3000 | Source: Anywhere

Type: Custom TCP | Port: 3001 | Source: Anywhere

Type: Custom TCP | Port: 3002 | Source: Anywhere

Type: SSH | Port: 22 | Source: Your IP (for security)

Click Launch Instance 

**** -----------------------------------***
3. Update System 
sudo apt update && sudo apt upgrade -y

4. Install Docker
5. sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

 5. Install Docker Compose
    sudo apt install curl -y
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

****------------------------------****
 docker-compose up -d 
 9. Access Application

Frontend Dashboard: http://<public-ip>:3000

Development API: http://<public-ip>:3000/dev

Production API: http://<public-ip>:3000/prod 

I have attached the image in asset




