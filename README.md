## deploy-flaskapp-on-vagrant-via-ansible

Ansible deploys Flask app on a Vagrant VM. 
Ansible is used as a provisioner to install and configure the VM. 
Just typing "vagrant up", the app will be running and reachable on 
http port 80 at http://192.168.33.15 and http://devops.adsnative.com.

Steps:
  - The provisioner cloned [this github repo](https://github.com/picatcha/adsnative_devops_challenge) into the VM under `/webapps/adsnative`
  - Packages installed : git, python-pip, nginx, gunicorn, flask, and redis.
  - The app code in the repo not touched
  - The app will be automatically restarted if crashes or is killed via upstart.
  - The app maxmimize all of the available CPUs - via 'nproc' command in Vagrantfile.
  - The app's logs are captured to `/var/log/adsnative/app.log` with hourly logrotate - /etc/cron.daily/logrotate, /etc/logrotate.d/adsnative
  - Timezone set to US EST.

Note:
  - Accessing the app with http://devops.adsnative.com requires /etc/hosts setup in hosting machine.
