## Introduction
this is the installation guide for Ubuntu 16.04 LTS as of 2019.
This may not work in the future anymore tho, at least I'd like to write down the procedure I took this time.

## Tools
- Git/CCSM(unity manager)
```shell
sudo apt-get install git compizconfig-settings-manager
```

- [Set the Menu at the Bottom](http://ubuntuhandbook.org/index.php/2016/03/ubuntu-16-04-move-unity-launcher-to-bottom/)
```shell
gsettings set com.canonical.Unity.Launcher launcher-position Bottom
```

- [Arch-like Dark theme](https://itsfoss.com/install-themes-ubuntu/)


- Login to Git
```shell
git config --global user.name "YOUR_USERNAME"
git config --global user.email "your_email_address@example.com"
```

- Pycharm
`sudo snap install pycharm-community --classic`

- Sublime
`sudo snap install sublime-text  --classic`

- [Typora](https://typora.io/#linux)
- ~~ About Themes: [1](https://support.typora.io/About-Themes/) / [2](https://theme.typora.io/) ~~
  - ~~ [Monokai theme!](https://theme.typora.io/theme/Light-Monokai/) ~~


- [Anaconda](https://docs.anaconda.com/anaconda/install/linux/)

- [Language Setting: JP](https://moritzmolch.com/2287)

- Python3.6
```shell
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.6 python3.6-dev
```

- Pip for Python3.6
```shell
sudo apt-get install curl
curl https://bootstrap.pypa.io/get-pip.py | sudo -H python3.6
```

- Install Nvidia Driver on Ubuntu(then you will be able to connect to External Monitor!)
Check this link as well: https://www.tensorflow.org/install/gpu

- Install MuJoCo
Mianly follow this link: https://github.com/openai/mujoco-py#install-mujoco
```shell
unzip mujoco200_linux.zip
mkdir ../.mujoco
sudo mv mujoco200_linux ../.mujoco/mujoco200
mv mjkey.txt ../.mujoco/
rm mujoco200_linux.zip
git clone https://github.com/openai/mujoco-py.git
cd mujoco-py/
sudo pip3.6 install -e .
```

Add the following lines in `~/.bashrc`
```bash
alias home="cd ~/Desktop"

# MuJoCo
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/norio0925/.mujoco/mujoco200/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/nvidia-410
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libGLEW.so
```

Then run the following commands to install missing modules on Ubuntu
```shell
sudo apt install libx11-dev libglew-dev patchelf
```

## Other Miscellenius tools/settings
- [CPU usage on menu bar](https://askubuntu.com/questions/406204/how-can-i-add-the-current-cpu-usage-to-my-menu-bar-as-a-percentage)
```shell
sudo apt install indicator-multiload
# then open the system indicator and modify the indicator items
```

- On pycharm, to use MuJoCo, you need to manually set the environmental path. So that set the following line to `Environment Variables` in `Run/Degub Configurations` to enable python see them on Pycharm
```shell
PYTHONUNBUFFERED=1;LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/norio0925/.mujoco/mujoco200/bin:/usr/lib/nvidia-410;LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libGLEW.so
```
- if you come across this error: `UserWarning: Matplotlib is currently using agg, which is a non-GUI backend, so cannot show the figure. plt.show()` then do the following line

```shell
sudo apt-get install tcl-dev tk-dev python3.6-tk
```

- when you get stuck at Proxy issue(`fatal: Unable to look up github.com (port 9418)`) in doing pip. try this

```shell
git config --global url."https://".insteadOf git://
```

## Pip list
- for OpenAI/Gym, consider using my repo for this
https://github.com/Rowing0914/gym_modified
- other than that, follow below
`sudo pip3.6 install matplotlib tensorflow-gpu==1.14.0 tensorflow-probability pandas opencv-python atari_py`
