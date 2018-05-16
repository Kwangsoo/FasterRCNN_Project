# FasterRCNN Project on Google Cloud
  Working on progress....

## Getting Started

Here is the list of steps to create and configure the Google Cloud
1. Create VM Instance
2. Install CUDA-9.0 on a fresh installation of Ubuntu 16.04
3. How To Install and Use Docker on Ubuntu 16.04

## 1. Create VM Instance

### Prerequisites - Registration

First, go to https://cloud.google.com/ (Figure 1) and login with your google account
<div align="center">
  <img src="/Docs/login.PNG" width="200px" />
  <p>Google Login</p>
</div>

### Follow this Google Cloud Tutorial 
* [Google Cloud Tutorial]("https://github.com/Kwangsoo/FasterRCNN_Project/Docs/GoogleCloudTutorial.pdf") 


## 2. Install CUDA-9.0 on a fresh installation of Ubuntu 16.04

### Install Nvidia CUDA-9.0 on Ubuntu 16.04

- OS: Ubuntu 16.04 x86_64
- (Optional) Uninstall old version CUDA Toolkit such as:

```
sudo apt-get purge cuda
sudo apt-get purge libcudnn6
sudo apt-get purge libcudnn6-dev
```

- Install CUDA Toolkit 9.0 and cuDNN 7.0 as follows:

```
wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.0.176-1_amd64.deb
wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libcudnn7_7.0.5.15-1+cuda9.0_amd64.deb
wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libcudnn7-dev_7.0.5.15-1+cuda9.0_amd64.deb
wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libnccl2_2.1.4-1+cuda9.0_amd64.deb
wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libnccl-dev_2.1.4-1+cuda9.0_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1604_9.0.176-1_amd64.deb
sudo dpkg -i libcudnn7_7.0.5.15-1+cuda9.0_amd64.deb
sudo dpkg -i libcudnn7-dev_7.0.5.15-1+cuda9.0_amd64.deb
sudo dpkg -i libnccl2_2.1.4-1+cuda9.0_amd64.deb
sudo dpkg -i libnccl-dev_2.1.4-1+cuda9.0_amd64.deb
sudo apt-get update
sudo apt-get install cuda=9.0.176-1
sudo apt-get install libcudnn7-dev
sudo apt-get install libnccl-dev
```

- Restart the VM Instance to load the NVIDIA drivers.

## 3. How To Install and Use Docker on Ubuntu 16.04

### Installing docker
Next, we will install docker. Docker has two available editions: Community Edition (CE) and Enterprise Edition (EE). And just like NVIDIA driver, you need to know what Linux distribution you are using to choose the proper installation file. Below is the installing instructions for Docker Community Edition on Ubuntu (the OS I am using, of course).

Firstly, you need to remove (if any) old version of docker. If you can assure that this is the first time you install docker on your machine, then you can skip to the next step. Otherwise, you’d better run the following command:
```
$ sudo apt-get remove docker docker-engine docker.io
```

If docker is not installed on your machine, then apt-get will tell you that. It is totally fine.

Next, we will install docker. I recommend installing docker using the repository so that when the new version is available, you can get the update from repository easily.

To installing from repository, we need to set up the Docker repository first. As usual, you may want to update the apt package index:
```
$ sudo apt-get update
```

Next, install the packages to allow apt to use a repository through HTTPS:
```
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

Next, add the official GPG key of Docker:
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Verify that the command below print out 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88:
```
$ sudo apt-key fingerprint 0EBFCD88
```

Next, tell apt to use the stable repository by run the command below:
```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

At this point, we have finished set up the repository. Next, we will update the apt package index and install Docker CE:
```
$ sudo apt-get update && apt-get install docker-ce
```

Next, we will check if Docker is installed correctly by running the well-known hello-world Image:
```
$ sudo docker run hello-world
```


### Installing NVIDIA docker
In the next step, we will finish our job by installing NVIDIA docker, which is just a plug in of Docker to help container use the GPUs of the host machine.

First, you need to remove NVIDIA docker 1.0 (if installed):

docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
sudo apt-get purge -y nvidia-docker
Next, we will add the necessary repository, then update the apt package index:
```
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update
```

We are nearly there, next we will install NVIDIA docker:
```
sudo apt-get install -y nvidia-docker2
sudo pkill -SIGHUP dockerd
```

That’s it. We have installed NVIDIA docker. Let’s verify the installation by running the latest CUDA image, which is officially provided by NVIDIA:
```
docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi
```

If this is the first time you run the command above, you might notice that Docker is trying to download 



Remember that Docker somehow works the same way as VM? It means that in order to create Containers, Docker first needs an Image too. And where is it getting the Image from? Well, I will make it clear in the next blog post. After the Image is downloaded and the command is executed





## Running the tests

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone who's code was used
* Inspiration
* etc


## Please check the original ReadMe file
See the original readme file [ReadMe.md](https://github.com/Kwangsoo/FasterRCNN_Project/blob/master/README_Default.md) 
<div align="center">
  <img src="demo/output/33823288584_1d21cf0a26_k_example_output.jpg" width="700px" />
  <p>Example Mask R-CNN output.</p>
</div>

