First, install supervisord using apt-get package.

Then go to this path `/etc/supervisor/conf.d/` and create a file named `celery.conf` .

Write the following command to `celery.conf`  
```
[program:celery]
directory = /home/ubuntu/prod/api
command = /home/ubuntu/anaconda3/envs/api_env/bin/celery -A prodapi worker -l info --without-gossip --without-mingle --without-heartbeat -Ofair --pool=solo   
stdout_logfile=/var/log/supervisor/celery.log    
stderr_logfile=/var/log/supervisor/celery.log
user=ubuntu
```                                                                                                                                                  
Then to start it working write this command  `supervisorctl restart celery`             
