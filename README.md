# Network configuration : project1 <--> project2 <--> project3
# project1 and project3 are isolated

1. docker build -t project1 -f project1/Dockerfile ./project1
2. docker build -t project2 -f project2/Dockerfile ./project2
3. docker build -t project3 -f project3/Dockerfile ./project3
4. docker network create net1
5. docker network create net2
6. docker run --name project1 --network net1 -p 8081:80 project1
7. docker run --name project2 --network net1 -p 8082:80 project2
8. docker run --name project3 --network net2 -p 8083:80 project3
9. docker network connect net2 project2