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


### Follow this Google Cloud Tutorial 
* [Google Cloud Tutorial](https://github.com/Kwangsoo/FasterRCNN_Project/Docs/Google Cloud Tutorial.pdf) 


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

