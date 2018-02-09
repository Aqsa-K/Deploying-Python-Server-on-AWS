# Deploying-Python-Server-on-AWS
Steps/commands on how to easily deploy a python server on your AWS Ubuntu machine using PUTTY 

## Dependencies required:
### Python3
```
sudo apt-get upgrade
sudo apt-get update
sudo apt-get install python3
```

### Pip
```
sudo apt-get install python3-setuptools
sudo apt-get install python3 pip
pip3 install --upgrade pip
```
Perform the last step only when an upgrade is required

### TensorFlow
```
sudo apt-get install python3-pip python3-dev
pip3 install tensorflow
```
OR
```
sudo pip3 instal ---upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.2.1-cp27-none-linux_x86_64.whl
```

### For downloading any other dependency
For example we require Google-auth 
```
sudo pip3 install google-auth
```

## Set 'starter.sh' file
Call your run.py file through a separate text file with an arbitrary name such as starter.sh and save it in your projects git repository

Add `#!/bin/sh` as the first line of your code in `starter.sh` file 

Try executing your starter.sh file by `sudo starter.sh` to make sure there are no errors in execution steps

## PUTTY
Start your session on PUTTY

Clone your git repository
```
git clone 'link to repository'
```

## Automatic startup of run.py file
To make sure your run.py is automatically run whenever the AWS machine restarts you'll have to add the path to your rc.local script. 

Following are the steps:

Provide your `/etc/rc.local script` with the full path and name of your createrd scrit after the 'sh' command - (your etc folder will be in the outermost directory)

Use vim to edit your rc.local script
```
sudo vim rc.local
```
Put the following line before the last line of code (`exit 0`) at the end of the /etc/rc.local script
```
sh '/path/to/your/script/starter.sh'
```



