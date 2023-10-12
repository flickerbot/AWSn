install cloudwatchlogs agent

> curl https://s3.amazonaws.com/aws-cloudwatch/downloads/latest/awslogs-agent-setup.py -O

> curl https://s3.amazonaws.com/aws-cloudwatch/downloads/latest/AgentDependencies.tar.gz -O

>
tar xvf AgentDependencies.tar.gz -C /tmp/ 	

the next command requires python to be installed so install python
> apt-get install python

> sudo python ./awslogs-agent-setup.py --region us-east-1 --dependency-path /tmp/AgentDependencies

You can install the CloudWatch Logs agent by specifying the us-east-1, us-west-1, us-west-2, ap-south-1, ap-northeast-2, ap-southeast-1, ap-southeast-2, ap-northeast-1, eu-central-1, eu-west-1, or sa-east-1 Regions.


The CloudWatch Logs agent installer requires certain information during setup. Before you start, you need to know which log file to monitor and its time stamp format. You should also have the following information ready.


take it from here
https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/QuickStartEC2Instance.html



## follow the procedure and give the give the path to pm2 logs 

Genrally it is 
> /root/.pm2/pm2.log



now goto
> /var/awslogs/etc/awslogs.conf 

and check the path has been added or not at end like this 


```
[root/.pm2/pm2.log]
datetime_format = %b %d %H:%M:%S
file = /root/.pm2/pm2.log
buffer_duration = 5000
log_stream_name ={instance_id}
initial_position = start_of_file
log_group_name = pm2logs

```
Now run this command to start the awslogs service 

> sudo service awslogs restart

run this command to check the logs are being pushed successfully 
> sudo cat /var/log/awslogs.log



done ;) 








