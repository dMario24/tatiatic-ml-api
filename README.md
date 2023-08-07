# tatiatic-ml-api
- https://tatiatic-ml-api.fly.dev/docs
  
## ENV
- python 3.9

- pyenv
```
$ pyenv install --list
$ pyenv install 3.9.16
$ pyenv global 3.9.16
$ pyenv versions
pyenv versions
  system
  3.7.16
* 3.9.16 (set by /home/tom/.pyenv/version)
```

- pipenv
```
$ pip install pipenv
$ pipenv --python 3.9.16
$ pipenv shell
```

## DEV
```
$ pipenv shell
$ pipenv install fastapi
$ pipenv install "uvicorn[standard]"
```

## RUN
- uvicorn app.main:app --reload

## DEPLOY
### docker
``` bash
# Generate a requirements.txt from Pipfile.lock.
$ pipenv requirements > requirements.txt

$ docker build -t tatiatic-ml-api:0.1.0 .
$ docker images tatiatic-ml-api
REPOSITORY        TAG       IMAGE ID       CREATED          SIZE
tatiatic-ml-api   0.1.0     9c4500f3f26a   28 seconds ago   1.05GB

$ docker run -d --name tatiatic-ml-api-010 -p 5010:8080 tatiatic-ml-api:0.1.0
$ docker ps
CONTAINER ID   IMAGE                   COMMAND                  CREATED          STATUS          PORTS                    NAMES
e63bf91b996f   tatiatic-ml-api:0.1.0   "uvicorn app.main:ap…"   26 seconds ago   Up 25 seconds   0.0.0.0:5010->8080/tcp   tatiatic-ml-api-010
```

### fly.io
``` bash
$ fly deploy
==> Verifying app config
Validating /Users/m2/code/tatiatic-ml-api/fly.toml
Platform: machines
✓ Configuration is valid
--> Verified app config
==> Building image
Remote builder fly-builder-floral-cloud-2484 ready
==> Building image with Docker
--> docker host: 20.10.12 linux x86_64
[+] Building 18.4s (10/10) FINISHED                                                                                                                
 => [internal] load build definition from Dockerfile                                                                                          0.2s
 => => transferring dockerfile: 280B                                                                                                          0.2s
 => [internal] load .dockerignore                                                                                                             0.2s
 => => transferring context: 49B                                                                                                              0.2s
 => [internal] load metadata for docker.io/library/python:3.9                                                                                 0.6s
 => [internal] load build context                                                                                                             0.3s
 => => transferring context: 1.05kB                                                                                                           0.3s
 => [1/5] FROM docker.io/library/python:3.9@sha256:fdff20fe1b98766e020a4dd5ad4537e6753e5de7cc40737d8b713647e088d5a4                          10.5s
 => => resolve docker.io/library/python:3.9@sha256:fdff20fe1b98766e020a4dd5ad4537e6753e5de7cc40737d8b713647e088d5a4                           0.0s
 => => sha256:785ef8b9b236a5f027f33cae77513051704c0538bff455ff5548105c954c3b1c 49.56MB / 49.56MB                                              2.2s
 => => sha256:5a6dad8f55ae6c733e986316bd08205c8b2c41640bf8d08ff6e9bbcb6884304f 24.03MB / 24.03MB                                              3.1s
 => => sha256:bd36c7bfe5f4bdffcc0bbb74b0fb38feb35c286ea58b5992617fb38b0c933603 64.11MB / 64.11MB                                              3.7s
 => => sha256:4d207285f6d296b9806bd00340437406c25207412c52fcfcbf229a5ecff7bf94 211.03MB / 211.03MB                                            5.2s
 => => sha256:cc429e3ed9d513cf41bcb2eab70a546fbc31985e672e3de090d9add84fede64c 245B / 245B                                                    0.0s
 => => sha256:eb752ab36a047e17ebc1cf671ff4d12060c28d13219ae781b669c326eceffe3d 2.85MB / 2.85MB                                                0.1s
 => => sha256:fdff20fe1b98766e020a4dd5ad4537e6753e5de7cc40737d8b713647e088d5a4 1.86kB / 1.86kB                                                0.0s
 => => sha256:60d390c1959be040e1e9cfd6bf9a9684c77ed37c3d2949386c2687f8109af11d 7.51kB / 7.51kB                                                0.0s
 => => sha256:6fa59a7ce94bf6afe931a6c66af9413d6ad4be2bad39f107648373c1f9310235 15.82MB / 15.82MB                                              0.3s
 => => sha256:3d35a404db586d00a4ee5a65fd1496fe019ed4bdc068d436a67ce5b64b8b9659 2.01kB / 2.01kB                                                0.0s
 => => sha256:9402da1694b8dae94a0cb89a2719ce24a909e809b22c31d39edee8e18b3d300b 6.39MB / 6.39MB                                                0.2s
 => => extracting sha256:785ef8b9b236a5f027f33cae77513051704c0538bff455ff5548105c954c3b1c                                                     1.4s
 => => extracting sha256:5a6dad8f55ae6c733e986316bd08205c8b2c41640bf8d08ff6e9bbcb6884304f                                                     0.4s
 => => extracting sha256:bd36c7bfe5f4bdffcc0bbb74b0fb38feb35c286ea58b5992617fb38b0c933603                                                     1.5s
 => => extracting sha256:4d207285f6d296b9806bd00340437406c25207412c52fcfcbf229a5ecff7bf94                                                     3.8s
 => => extracting sha256:9402da1694b8dae94a0cb89a2719ce24a909e809b22c31d39edee8e18b3d300b                                                     0.2s
 => => extracting sha256:6fa59a7ce94bf6afe931a6c66af9413d6ad4be2bad39f107648373c1f9310235                                                     0.3s
 => => extracting sha256:cc429e3ed9d513cf41bcb2eab70a546fbc31985e672e3de090d9add84fede64c                                                     0.0s
 => => extracting sha256:eb752ab36a047e17ebc1cf671ff4d12060c28d13219ae781b669c326eceffe3d                                                     0.1s
 => [2/5] WORKDIR /code                                                                                                                       0.0s
 => [3/5] COPY ./requirements.txt /code/requirements.txt                                                                                      0.0s
 => [4/5] RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt                                                                  6.8s
 => [5/5] COPY ./app /code/app                                                                                                                0.0s
 => exporting to image                                                                                                                        0.3s
 => => exporting layers                                                                                                                       0.3s
 => => writing image sha256:862cb84f865895ac363488315a4c9e9d3727b97d4e4a7288395bbaa11699adb9                                                  0.0s
 => => naming to registry.fly.io/tatiatic-ml-api:deployment-01H785FAHAAVR24BBA9BTHR7KF                                                        0.0s
--> Building image done
==> Pushing image to fly
The push refers to repository [registry.fly.io/tatiatic-ml-api]
269975bac158: Pushed 
b18f894c6107: Pushed 
710621e79ff3: Pushed 
64b786ffcc82: Pushed 
efe0d4175e55: Pushed 
c387ce904bb7: Pushed 
cf3ce544b9f4: Pushed 
c5f1d4dd95f0: Pushed 
6a25221bdf24: Pushed 
b578f477cd5d: Pushed 
b298f9991a11: Pushed 
c94dc8fa3d89: Pushed 
deployment-01H785FAHAAVR24BBA9BTHR7KF: digest: sha256:a7aa9914a6c61ab301aceae6405bb3ffd30a551018e0ee4291f18b7c2ff949c5 size: 2839
--> Pushing image done
image: registry.fly.io/tatiatic-ml-api:deployment-01H785FAHAAVR24BBA9BTHR7KF
image size: 1.0 GB

Watch your app at https://fly.io/apps/tatiatic-ml-api/monitoring

Provisioning ips for tatiatic-ml-api
  Dedicated ipv6: 2a09:8280:1::69:5053
  Shared ipv4: 66.241.125.251
  Add a dedicated ipv4 with: fly ips allocate-v4
This deployment will:
 * create 2 "app" machines

No machines in group app, launching a new machine
  Machine 3d8d9ee1a27408 [app] update finished: success
Creating a second machine to increase service availability
  Machine e2865110a75028 [app] update finished: success
Finished launching new machines

NOTE: The machines for [app] have services with 'auto_stop_machines = true' that will be stopped when idling


Visit your newly deployed app at https://tatiatic-ml-api.fly.dev/
```

## REF
- https://fastapi.tiangolo.com/ko/
- https://fastapi.tiangolo.com/deployment/docker/#dockerfile
