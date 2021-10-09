# Troubleshooting-service-Docker

Steps to troubleshoot a service Which is unable to deploy-

```
1. Use the following command to list all the services running in the swarm:
$ sudo docker service ls

2. Use the following command to inspect a service for configurations:
$ sudo docker service inspect <Service name>

3. List the tasks assigned for a given service to determine whether they are currently running or not
$ sudo docker service ps <Service name>

4. Use the following command to install jq package which is a JSON processor:
$ sudo apt install jq

5. Use the following command to inspect a specific task to determine which container is associated with the given service:
$ sudo docker inspect TASK_ID | jq -r \
> '.[].Status.ContainerStatus.ContainerID'
Note: Replace TASK_ID with the Id of a selected task. 

6. Use the following command to get the container state:
$ sudo docker inspect CONTAINER_ID | jq '.[].State'
Note: Replace CONTAINER_ID with the first 12 characters of container Id received in the previous step. 
Note: ExitCode and Error show the reasons why a container has made an exit

7. Use the following command to check the Network Settings of the container:
$ sudo docker inspect CONTAINER_ID | jq '.[].NetworkSettings'
Note: Replace CONTAINER_ID with the first 12 characters of container Id received in the previous step. 

8. Use the following command to get detailed logs of redis service:
$ sudo docker service logs <Service name>

```
