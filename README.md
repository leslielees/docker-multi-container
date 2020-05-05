# docker-multi-container

We will learn how to deploy multi container docker in the lession.

A web app to call api to return some computed no which is managed by worker and cached and persisted.

So,

Web app
Worker
API
Redis
DB

We can cross include any of service of docker-composed containers by simply refering to its name.

For multi container deps, its not recomm to put in EB

Instead, it should be push to docker hub via Travis and then let AWS to pull from docker hub

## Dockerrun.aws.json

For multi container deployment to AWS. This is requird which is similar to docker-compose file.

```
Docker-compose - instrctun to how to build images
Dockerrun.aws.json - Specific file name for deplyong images to AWS.
```

Elastic Beanstalk will forward any instruction to ECS - > Elastic Container Service

ECS has set of task definitions which tell how to run a task.

Now, we need to follow this syntax to be able to qualify Dockerrun.aws.json container definitsion.

[Task Definition/Container definitions Docs](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html#container_definitions)

`hostname refers  service name in compose file`

`essential : true makes if any containr fail, everything will fail in dep`

Atleast 1 container definition must be true