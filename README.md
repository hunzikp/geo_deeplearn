# Docker image for deep learning on geo-spatial imagery

## Requires

* [nvidia-docker](https://github.com/NVIDIA/nvidia-docker)

## Features

* Built on ubuntu 16.04 with CUDA 8.0 and cudnn 6
* Python 3.5.2
    - tensorflow and keras (GPU enabled)
    - scikit-learn, scikit-image, pandas
    - Jupyter Notebook
    - pycharm community (2017.3)
* R (most recent)
    - sf, raster, velox (including system dependencies)
    - tensorflow for R
    - RStudio Server (1.1.383)
* git & subversion

## Usage

Run container in background with GUI support:
```shell
nvidia-docker run -td -u coder -p 8787:8787 -p 8888:8888 -p 8008:8008 -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:ro geo_deeplearn
```

Option | Descr
--- | ---
`-td` | makes sure container runs in background
`-u coder` | login as user 'coder'
`-e` and `-v` | ensure GUI support (for pycharm)
`-p 8787:8787`| port forwarding for rstudio
`-p	8888:8888` | port forwarding for jupyter
`-p 8008:8008` | port forwarding for tensorboard

Don't forget to run `xhost +` on local machine for GUI support [warning: not safe].

Enter the running container:
```shell
docker exec -it [container_id] bash 
```

Start the Rstudio Server
```shell
sudo rstudio-server start
```

Start Jupyter Notebook
```shell
jupyter notebook --ip=0.0.0.0 --no-browser
```

Start pycharm
```shell
pycharm
```

