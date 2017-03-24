# gitlab-shell-runner

Here's how to use this runner as a docker swarm service:

```bash
docker service create \
--constraint 'node.role == manager' \
--name gitlab-shell-runner \
--mount type=bind,source=/var/run/docker.sock,destination=/var/run/docker.sock \
gitlab-shell-runner:latest http://git.example.org YourGitlabToken
```

You can also use all gitlab-runner environment variables like RUNNER_NAME or RUNNER_TAG_LIST.

By running the gitlab-runner on the manager nodes, we can easily manage our swarm.
So it's easy to create images and update services.
