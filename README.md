[![<mohammedx3>](https://circleci.com/gh/mohammedx3/project.svg?style=svg)](https://app.circleci.com/pipelines/github/mohammedx3/project)
  
### Files:
app.py: The web app written in python
Makefile: Setup the environment, lint app.py and Dockerfile and finally to install depenadcies needed from requirements.txt.
Dockerfile: Has Docker configuration and copies the app to a working directory and install requirments
requirments.txt: Includes the needed libraries for the project.
run_docker.sh: To start the app on a container.
run_kubernetes.sh: To start the app on Kubernetes.
upload_docker.sh: Uploads the image to a docker hub repo.
 
hadolint-Linux-x86_64  Makefile  make_prediction.sh  model_data  output_txt_files  README.md  requirements.txt  run_docker.sh  run_kubernetes.sh  upload_docker.sh

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Running `app.py`on Docker
#Builds the image then run it

docker build --tag=api .
docker run -p 8000:80 api

### Running `app.py`on Kubernetes
dockerpath=mohammedx3/project << docker image path

kubectl run api\
    --generator=run-pod/v1\
    --image=$dockerpath\
    --port=80 --labels app=api
