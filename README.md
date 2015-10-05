# Web Deployment with Docker and Digital Ocean

## Pushing a new version of the app
#### Build Image on Boot2Docker
1, Open Boot2Docker
2, cd into the root of your project (Check the branch)
3, Build the image:
```sh
docker build -t <account>/<repo>:<version> .
```
3, Push it to docker hub:
```sh
docker push <account>/<repo>:<version>
```

#### SSH into Digital Ocean Droplet
1, Check current containers running with
```sh
docker ps
```
2, Pull new image
```sh
docker pull <account>/<repo>:<version>
```
3, Stop old container app
```sh
docker stop <name of app running on port 80>
```
4, Get up the new container connection
```sh
docker run -it —name <name of app example: app7> -p 80:5000 <account>/<repo>:<version>
```
5, Start the new container
```sh
docker start <name of app>
```
6, Enter into the application
```sh
docker exec -it <name of app> bash
```
7, Install forever globally, to ensure script continues to run
```sh
npm install forever -g
```
8, Clean the front end build
```sh
npm run clean
```
9, Build a fresh copy
```sh
npm run build
```
10, exit application
```sh
exit
```
11, Start the app
```sh
docker exec -d <name of app> forever start server
```
