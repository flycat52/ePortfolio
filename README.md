# AWS EC2 setup env

launch Amazon Linux AMI 2017.09.0 (HVM) in EC2
chmod 400 angular.pem
sudo ssh -i angular.pem ec2-user@ec2-52-14-28-254.us-east-2.compute.amazonaws.com
sudo yum install git

# git

sudo git clone https://github.com/flycat52/ePortfolio.git
sudo git checkout -b adrian
sudo git push --set-upstream origin adrian
sudo git checkout -b a:drian
sudo git push --set-upstream origin adrian
sudo git add .
sudo git commit -m 'msg'
sudo git push
sudo git checkout master
sudo git merge adrian
sudo git push
sudo git config credential.helper store
sudo git push https://github.com/flycat52/ePortfolio.git

# Docker on EC2 AMI :

sudo yum update -y
sudo yum install -y docker
sudo service docker start
sudo usermod -a -G docker ec2-user
reboot instance
docker run --rm -p 5000:5000 beaconwarden/ecs1:latest
docker build -t ecs1 .
docker images --filter reference=ecs1
docker run -p 5000:5000 beaconwarden/ecs1
docker tag bb38976d03cf beaconwarden/ecs1:latest
docker commit containerID beaconwarden/ecs1:latest
docker push beaconwarden/ecs1
docker ps
docker images

docker rm $(docker ps -a -q) docker rmi $(docker images | grep "^" | awk "{print $3}")

C9 container

https://hub.docker.com/r/kdelfour/cloud9-docker/
docker pull kdelfour/cloud9-docker
docker run -it -d -p 80:80 -v /home/ec2-user/:/c9workspace/ kdelfour/cloud9-docker

reference :

https://blog.miguelgrinberg.com/post/designing-a-restful-api-with-python-and-flask
http://www.chartjs.org/docs/latest/getting-started/usage.html
http://flask.pocoo.org/docs/0.12/quickstart/#rendering-templates
http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html
https://github.com/jconning/lambda-cpu-cost
https://gist.github.com/Daniel-Hug/7273430
http://docs.aws.amazon.com/cli/latest/userguide/installing.html
https://docs.docker.com/engine/examples/dotnetcore/#create-a-dockerfile-for-an-aspnet-core-application
https://ropenscilabs.github.io/r-docker-tutorial/04-Dockerhub.html
