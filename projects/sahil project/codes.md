backend
--npm i
--node server.js

frontend
--npm i
-- npm run dev

node 20.5 
npm 10.8



so we install docker git nodejs docker-compose (DO NOT download nginx)

create ssh-keygen
id_rsa.pub expose to github

git clone private repo

--run the backend

dockerfile with docker compose for nginx

--run the frontend

cd frontend
npm run build
aws s3 sync s3://www.betabookmyshow.com --delete


in github actions
to expose the env files
- name: Create .env file
  run: |
    echo "DB_PASSWORD=${{ secrets.DB_PASSWORD }}" >> .env
    echo "API_KEY=${{ secrets.API_KEY }}" >> .env

- name: Run Docker Compose
  run: docker-compose up -d --build


version: '3.8'
services:
  backend:
    build: .
    ports:
      - "3000:3000"
    env_file:
      - .env
docker compose for env file



now, lets talk about where are we building the image for docker
-- inside the instance
-- inside the github actions

for inside the instance, itll just require docker compose down, docker compose rebuild, docker 
	compose up.
	
	--
	version: '3.8'

services:
  backend:
    image: myapp-backend  # Change to "mydockerhubuser/myapp-backend:latest" if pulling from Docker Hub
    build: .  # This line is used for on-device builds (ignored if pulling)
    ports:
      - "5000:5000"
    env_file:
      - .env  # Load environment variables
    restart: always
	--
	
	docker-compose down
docker-compose build --no-cache
docker-compose up -d


OR
services:
  backend:
    image: myapp-backend
    build:
      context: ./backend  # Path where the Dockerfile is located
      dockerfile: Dockerfile  # You can specify a different Dockerfile if needed
    ports:
      - "5000:5000"
    env_file:
      - .env
    restart: always

	
for github actions, itll require to create a dockerhub account and pushing it. and this will be more efficient because no load is done on the instance itself, and the website is always running

docker pull mydockerhubuser/myapp-backend:latest
docker-compose down
docker-compose up -d


take care of edge cases, like clearing out the old images and stuff, as they might take up space

docker-compose build --no-cache --force-rm if using instance build image
docker system prune -a


OR
you can always pull newer images with latest as its tag== 
services:
  backend:
    image: mydockerhubuser/myapp-backend:latest
    pull_policy: always  # Ensures latest image is fetched

this will not create old images, but willl replace them

docker image prune -a
still clear the images which are not being used.




now, onto the docker compose which uses the nginx for http and https, along with load balancing

------------
version: '3.8'

services:
  backend:
    build: ./backend  # Path to the Dockerfile of your backend
    container_name: backend
    restart: always
    environment:
      NODE_ENV: production
    ports:
      - "5000:5000"
    networks:
      - app-network

  nginx:
    image: nginx:latest
    container_name: nginx
    restart: always
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf:ro
      - /etc/letsencrypt:/etc/letsencrypt  # Mount SSL certificates
    depends_on:
      - backend
    networks:
      - app-network

networks:
  app-network:
    driver: bridge



------------



AND the nginx.conf file (make sure you are putting it at the right direcotry inside the instance)

-*-*-*-*-*-*

events {}

http {
    server {
        listen 80;
        server_name api.betabookmyshow.com;

        # Redirect all HTTP requests to HTTPS
        location / {
            return 301 https://$host$request_uri;
        }
    }

    server {
        listen 443 ssl;
        server_name api.betabookmyshow.com;

        ssl_certificate /etc/letsencrypt/live/api.betabookmyshow.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/api.betabookmyshow.com/privkey.pem;

        ssl_protocols TLSv1.2 TLSv1.3;
        ssl_ciphers HIGH:!aNULL:!MD5;

        location / {
            proxy_pass http://backend:5000;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
}


------------

be sure to create the ssl certificate the first time you create the instance

sudo apt update
sudo apt install certbot python3-certbot-nginx -y
sudo certbot certonly --nginx -d api.betabookmyshow.com


the certificates get created at
Successfully received certificate.
Certificate is saved at: /etc/letsencrypt/live/api.betabookmyshow.com/fullchain.pem
Key is saved at:         /etc/letsencrypt/live/api.betabookmyshow.com/privkey.pem

which is then used in nginx.conf

AND automatic renew in few days

sudo certbot renew --dry-run
sudo crontab -e

add this to the bottom of it-
	0 3 * * * certbot renew --quiet && systemctl reload nginx
and sudo systemctl restart nginx


done with backend.


docker-compose up -d --build



for questions:

check the chatgpt convo for Dockerfile MERN backend
