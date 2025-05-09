install docker
sudo dnf -y install docker

sudo systemctl start docker
sudo systemctl enable docker

sudo usermod -aG docker $USER
newgrp docker

dockerhub-username/repository-name:tag
docker build -t your-dockerhub-username/mern-backend:latest -f backend/Dockerfile backend/



remember the sed for changing the pulbic ip
find Frontend -type f -exec sed -i "s|http://[0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+:5555|http://${{ secrets.VPS_HOST }}:5555|g" {} +

check for connection
netstat -tulnp | grep 5173


(check the github actions)

the ssh public key needs to be in the authorised keys part
and private key needs to be in the github secrets


--- make sure that you are using environment variable as MONGODB_URL



db.books.insertMany(
    Array.from({ length: 7000 }, () => ({
        title: "Sample Title",
        author: "Author Name",
        publishYear: Math.floor(Math.random() * (2025 - 1900) + 1900),
        createdAt: new Date(),
        updatedAt: new Date(),
        __v: 0
    }))
);

sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose


aws s3 sync code
aws s3 sync dist/ s3://mern-frontend-project-1


----
docker compose file contians
version: "3.8"

services:
  nginx:
    image: nginx:latest
    container_name: nginx_proxy
    restart: always
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro
    depends_on:
      - backend

  backend:
    image: name
    restart: always
    environment:
      - MONGODB_URL=mongodb
    expose:
      - "5555"


----
nginx.conf contains 
                                                                     
events {}

http {
    upstream backend_servers {
    #docker backend container names
        server ec2-user-backend-1:5555;
        server ec2-user-backend-2:5555;
        server ec2-user-backend-3:5555;
    }

    server {
	listen 80;

        location / {
            proxy_pass http://backend_servers;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
}


we need to haev docker compose only

docker-compose down
docker-compose up -d --scale backend=3
and to check the nasmes of the docker containers 
docker ps
docker logs name_of_backend_container


//// make sure you change the file in frontend which has the public ip of the backend




sudo nano /etc/nginx/conf.d/backend.conf



in ubuntu to dowload 20th node
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs


generating key
ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
cat ~/.ssh/id_rsa.pub




