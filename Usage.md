## Command line options ##


The command line prompt is indicated by the **$** symbol.

List command line options with explanation:
```
$ apache-response-time -h
apache-response-time is a performance analysis tool for the apache web server.


Usage: ./apache-response-time [options]


Options:
 -a access.log, --access-log=access.log	Apache access log file
					(Default: /var/log/apache2/access.log)

 -d date regex, --date=date regex	Date regex e.g. 06/Jun/2009
					(Default: today)

 -o order,      --order-by=order	Order of results
					One of: time count call_time bytes
					(Default: count)

 -l limit,      --limit=limit		Limit number of ranked scripts
					(Default: 10)

 -s server,     --server=server		Domain name of web server
					(Default: none)

 -b bin_path,   --bin-path=bin_path	Path to script directory
					(Default: cgi-bin)

 -e extension   --extension=extension	Script file extension
					(Default: cgi)

 -h             --help			Help message


Examples:

 apache-response-time -o time -l 5 -s http://acme.com/ -b Rockets -e php

Top 5 php scripts, ordered by time, in the Rockets web application.
Example links will have the form: http://acme.org/Rockets/Drying_paint.php?page=7.


```


## Rank scripts by average response time per call ##

```
apache-response-time -o call_time
```


## Show top 25 scripts ##

```
apache-response-time -l 25
```


## Performance analysis for 6th June ##

```
apache-response-time -d 06/Jun/2009
```


## Python scripts under PeoplesFrontJudea directory on brian.com domain ##

```
apache-response-time -e py -b PeoplesFrontJudea -s http://brian.com
```


# Setting up a daily cron job #

One approach to improving web site performance is for a different developer to improve the slowest script everyday.  apache-response-time is ideally suited for producing these daily reports.

Edit the crontab:
```
crontab -e
```

Example daily (Sun-Thurs) crontab entry:
```
#*     *    *    *    *  command to be executed
#-     -    -    -    -  -
#|     |     |     |     |
#|     |     |     |     +----- day of week (0 - 6) (Sunday=0)
#|     |     |     +------- month (1 - 12)
#|     |     +--------- day of month (1 - 31)
#|     +----------- hour (0 - 23)
#+------------- min (0 - 59)
MAILTO=webmaster@acme.com

59     23  *   *    0-5  apache-response-time
```

List the crontab:
```
crontab -l
```

### See also ###

[apache-response-time installation guide](Installation.md).