# GitLab-CE

1. Export GITLAB_HOME fold mapper
```
export GITLAB_HOME=/srv/gitlab
```
2. Run gitlab-ce docker
```
sudo docker run --detach \
  --hostname 192.168.71.151 \
  --publish 4433:443 --publish 8929:8929 --publish 2222:22 \
  --name gitlab-ce \
  --restart always \
  --volume $GITLAB_HOME/config:/etc/gitlab \
  --volume $GITLAB_HOME/logs:/var/log/gitlab \
  --volume $GITLAB_HOME/data:/var/opt/gitlab \
  --shm-size 256m \
  gitlab/gitlab-ce:latest
```
3. Change gitlab-ce default port to 8929
```
// Enter docker
sudo docker exec -it gitlab-ce /bin/bash

// Open gitlab.rb
vi /etc/gilab/gitlab.rb

// change external_url

// save with :wq!

// reconfigre
gitlab-ctl reconfigure
```
