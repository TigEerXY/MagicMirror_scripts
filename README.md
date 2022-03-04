# MagicMirror_scripts
Magic Mirror installation and setup scripts

these scripts can be used to automate installation of release upgrades.

# Install MagicMirror

## raspberry.sh  is the installation script, upgraded from the core package
to execute the install script, copy/paste this line into the terminal window on your device (I can't say PI, cause it works in a lot of other places too)

the bullseye special version has been merged into the only version


````bash
bash -c  "$(curl -sL https://raw.githubusercontent.com/sdetweil/MagicMirror_scripts/master/raspberry.sh)"
````
there is a log file, ~/install.log, created so we can be able to diagnose any problems

# Update to next MagicMirror version from an existing MagicMirror installation

## upgrade-script.sh will do the git pull and npm install, and refresh npm setup for any modules that might need it
it should handle all the work…<br>

#### and give you a trial run of all that, only applying changes if u request them


give it a try

this works on Mac as well, copy/paste this line into the terminal window on your device

````bash
bash -c  "$(curl -sL https://raw.githubusercontent.com/sdetweil/MagicMirror_scripts/master/upgrade-script.sh)"
````
## no changes are made to the local repo or the working copy

## if you WANT to actually apply the changes, copy/paste this line into the terminal window on your device

````bash
bash -c  "$(curl -sL https://raw.githubusercontent.com/sdetweil/MagicMirror_scripts/master/upgrade-script.sh)" apply
````
there is a log file (upgrade.log)  in the MagicMirror/installers folder…

# additional scripts that may be useful

## the install has two sections of additional support I have provided those separately too, in case u need to run one separately, or changed your mind after install

### turn off screen saver and setup pm2 to autostart MM on boot..

screensaveroff.sh, copy/paste this line into the terminal window on your device

````bash
bash -c "$(curl -sL https://raw.githubusercontent.com/sdetweil/MagicMirror_scripts/master/screensaveroff.sh)"
````
fixuppm2.sh, copy/paste this line into the terminal window on your device

````bash
bash -c "$(curl -sL https://raw.githubusercontent.com/sdetweil/MagicMirror_scripts/master/fixuppm2.sh)"
````

# Updating Magic Mirror
````bash
sudo git pull && npm install
````
If you are getting
"error: Your local changes to the following files would be overwritten by merge:
        installers/mm.sh
        package-lock.json
Please commit your changes or stash them before you merge."
Solution:
If you want remove all local changes - including files that are untracked by git - from your working copy, simply stash them:
````bash
sudo git stash push --include-untracked
````
If you don't need them anymore, you now can drop that stash:
````bash
sudo git stash drop
````

# Controlling you MagicMirror via PM2.

With your MagicMirror running via PM2, you have some handy tools at hand:

Show running instances
````bash
pm2 status
````

*** Remember to SAVE PM2 if instance has been modified ***
````bash
pm2 save
````

Restarting your MagicMirror
````bash
pm2 restart MagicMirror
````

Stopping your MagicMirror
````bash
pm2 stop MagicMirror
````

Show the MagicMirror logs
````bash
pm2 logs MagicMirror
````

Show the MagicMirror process information
````bash
pm2 show MagicMirror
````

