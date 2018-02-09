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

Use vim to edit your rc.local script:
```
sudo vim rc.local
```

Put the following line before the last line of code (`exit 0`) at the end of the /etc/rc.local script
```
sh '/path/to/your/script/starter.sh'
```

Check that the first line of `etc/rc.local script` is:
```
#!/bin/sh -e
```

Go to your outermost directory

Check that it has 'etc' and 'home' folders:

```
ls
```
The above command displays all folders in the current command


Make your `/etc/rc.local` script executable in case it is not already executable by:
```
sudo chown root /etc/rc.local
sudo chmod 755 /etc/rc.local
```

Check everything works fine by executing:
```
sudo /etc/init.d/rc.local start
```
This should start the starter.sh file and hence, the run.py file being called in starter.sh file

That is, your run.py file should start running, it should be executed by this step


Check that the process has actually started:
```
ps -ef
```
This should display all the processes currently running on the AWS machine


You can also check the running instances of only run.py process:
```
ps ax | grep run.py
```


To check program output, open the nohup.out file:
```
sudo tail -f nohup.out
```

## Killing a process
To kill a process, use the process number:
```
ps ax | grep run.py
```
This will give the process number of run.py process
```
sudo kill process-number
```
This will kill the process even if it is running in the background as a nohup process

