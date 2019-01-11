# yarnLogCollection

The yarn log aggregation happens after the application has stopped but sometimes we do not want to wait till the application is done or to stop the application to gather the logs. Also at times we see the log aggregation itself fails due to different reasons. In all such scenarios we wanted if tehre was a simple way to pull all the container records. So far we have been doing it by going to individual nodes, and finding it through all the yarn logs for container logs for the application which is not only very in-efficient but very tedious task to accomplish.

This utility script uses the RM REST API approach to first figure out the nodes having the container logs then uses the NM REST API to fetch the logs. So with this utility with one command you can pull the container logs for application at any point as long as the logs are thre on the nodes.


<h2>USAGE:</h2>
usage: logAggregate.py [-h] [--usekrb] [--spark] appid rmweburl [-o outputfile]

Example:- 
#./collectyarnlog.py  application_1544005654695_0002 https://nightly513-2.vpc.cloudera.com:8090/ -o application_1544005654695_0002.txt
  
  
./containerlog.py  -h
usage: test.py [-h] [--usekrb5] [--spark] [-o OUTPUTFILE] appid rmweburl

positional arguments:
  appid                 Provide the application id
  rmweburl              The url for the active RM

optional arguments:<p>
  -h, --help            show this help message and exit<p>
  --usekrb5             Use kerberos(spenego) to interact with RM and NM
                        usekrb if kerberos is enabled for the web interface<p>
  --spark               Optionali flag to tell it is spark application. This
                        avoid getting syslog if it is a spark application else
                        an Exception message gets logged for not able to fetch
                        syslog file as there is no syslog file on disk<p>
  -o OUTPUTFILE, --outputfile OUTPUTFILE
                        The output file to write logs. If not specified the
                        logs will be written to stdout
