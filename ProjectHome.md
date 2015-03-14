**apache-response-time** is a performance analysis tool for the apache web server.  It's primary focus is on script response time.

One approach to improving web site performance is for a different developer to improve one of the slowest scripts everyday.  apache-response-time is ideally suited for producing daily reports for this purpose.  It will help you find long running, frequently accessed and large apache scripts.

## Analysis for a single script ##

A selection from a performance analysis report for a single script:
```
Script 2: scop.cgi	Calls/s: 0.133	Throughput: 69.51k/s
	pct	total	min	max	avg	95%	stddev	median
Calls	31.75	11462
Time	14.12	2123.07	0.12	2.23	0.19	0.44	0.25	0.15
Size	14.58	144.11M	7.34k	179.33k	12.87k	19.59k	5.41k	12.16k
Time range [07/Sep/2009:00:00:01 +0100] to [07/Sep/2009:23:59:53 +0100]

Min time:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?&sunid=151351
Median time:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?&sunid=20876
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?&sunid=27844
Max time:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?&sunid=153375

Min size:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=47094
Median size:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=139890
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=24136
Max size:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=53931
```


The main summary statistics are for apache response time (**Time**) and the **Size** of the script output.

[Description of statistial measures](Example#Statistical_measures.md)

Links for the smallest, largest, slowest and fastest apache requests are provided for each script.

## Ranked script list ##

By default apache-response-time produces a ranked list of statistics for 10 scripts.
```
Rank	Calls	Response time	R/Call	Size	Script
====	=====	===============	=======	=======	======
   1	21044	11966.72 79.60%	  0.569	259.23M	gene.cgi
   2	11462	 2123.07 14.12%	  0.185	144.11M	scop.cgi
   3	 1826	  410.30  2.73%	  0.225	15.28M	model.cgi
   4	 1458	  385.37  2.56%	  0.264	476.34M	gen_list.cgi
   5	  310	  147.65  0.98%	  0.476	93.73M	taxonomic_gen_list.cgi
```
This list can be ordered by **Calls**, **Response time**, **R/Call** (reponse time per call) or **Size**.


## Further information ##

[Example](Example.md) - typical apache-response-time output

[Installation](Installation.md) - how to install the apache-reponse-time command

[Usage](Usage.md) - apache-response-time usage examples

[Roadmap](Roadmap.md) - List of future changes and features

**apache-response-time** is ideal for running from a [daily cron job](Usage#Setting_up_a_daily_cron_job.md).

The [pt-query-digest](http://www.percona.com/doc/percona-toolkit/2.1/pt-query-digest.html) tool, from the [Percona toolit](http://www.percona.com/software/percona-toolkit) mysql utilities package, has been influential on the development of apache-response-time.

## See also ##

[TinyLogAnalyzer](http://pypi.python.org/pypi/TinyLogAnalyzer) - Command line utility for perform response time analysis onto HTTP access logs

[request-log-analyzer](https://github.com/wvanbergen/request-log-analyzer) - Simple command line tool to analyze request log files in various formats to produce a performance report

[ApacheTop](http://www.webta.org/projects/apachetop/) - curses-based top-like display for Apache information, including requests per second, bytes per second, most popular URLs, etc.

[wtop and logrep](http://code.google.com/p/wtop/) - "top" for Apache and other webservers, plus powerful log grepping

[modlogslow](http://code.google.com/p/modlogslow/) apache module to provide measures of the time period used for handling each request by the current process

[Open Directory - Computers: Software: Internet: Site Management: Log Analysis: Freeware and Open Source](http://www.dmoz.org/Computers/Software/Internet/Site_Management/Log_Analysis/Freeware_and_Open_Source/)

[List of web analytics software from wikipedia](http://en.wikipedia.org/wiki/List_of_web_analytics_software)