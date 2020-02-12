
# apache-response-time

apache-response-time is a performance analysis tool for the apache web 
server access log file. It's primary focus is on script response time.

If you like apache-response-time, give it a star!

**Maintainence Mode** This code is now fairly mature.  I don't plan on making
any further changes.  I might integrate your pull request or fix any bugs 
which crash the tool but I'm unlikely to respond to other issues.

# Table of contents

 * [Major output sections](#major-output-sections)
 * [Statistical measures](#statistical-measures)
 * [Example output](#example-output)
 * [Installation and configuration](#installation-and-configuration)
 * [Command line options](#command-line-options)
 * [Usage examples](#usage-examples)
 

# Major output sections

The command output can be broken down into 4 sections:

 * Overall
 * Ranked scripts
 * Detailed statistics
 * Frequently requested URLs

*Overall* - summary statistics for all scripts combined

*Ranked scripts* - summary statistics for each of the scripts separately

*Detailed statistics* - detailed statistics and example URLs for each script

*Frequently requested URLs* - 10 most frequently requested URLs

# Statistical measures

The main summary statistics are for apache response time (*Time*) 
and the *Size* of the script output.  

 * *pct* - as a percentage of all scripts
 * *total* - total script calls, response time or size
 * *min* - minimum response time or size
 * *max* - maximum 
 * *avg* - mean 
 * *95%* - 95th percentile
 * *stddev* - standard deviation
 * *median* - median

Secondary statistics are calculated for:

 * *R/Call* - the response time per call	
 * *Throughput* - bytes per second


# Example output

Example of the apache-response-time command output from an apache 
access log file containing hits to 5 scripts.

~~~~
$ apache-response-time -s http://supfam.org -d 07/Sep/2009

Overall:
	Calls: 36100	(Unique: 34436)	per sec: 0.42
	Throughput: 67.35k/s

		    total	min	    max	    avg	    stddev
	Time	15033.1	0.11	4.60	0.42	0.71
	Size	988.70M	4.99k	545.68k	28.05k	77.06k
Time range [07/Sep/2009:00:00:01 +0100] to [07/Sep/2009:23:59:53 +0100]


Rank	Calls	Response time	R/Call	Size	Script
====	=====	===============	=======	=======	======
   1	21044	11966.72 79.60%	  0.569	259.23M	gene.cgi
   2	11462	 2123.07 14.12%	  0.185	144.11M	scop.cgi
   3	 1826	  410.30  2.73%	  0.225	15.28M	model.cgi
   4	 1458	  385.37  2.56%	  0.264	476.34M	gen_list.cgi
   5	  310	  147.65  0.98%	  0.476	93.73M	taxonomic_gen_list.cgi


Script 1: gene.cgi	Calls/s: 0.244	Throughput: 22.18k/s
	    pct	    total	min	    max	    avg	    95%	    stddev	median
Calls	58.29	21044
Time	79.60	11966.7	0.12	4.60	0.57	1.91	0.95	0.57
Size	26.22	259.23M	4.99k	100.94k	12.61k	34.96k	9.84k	12.91k
Time range [07/Sep/2009:00:00:02 +0100] to [07/Sep/2009:23:59:51 +0100]

Min time:
http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=ns&seqid=(NCU04065.2)
Median time:
http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=hs&seqid=ENSP00000371842
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=05&seqid=gi%7C153952338%7Cref%7CYP_001398471.1%7C
Max time:
http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=up&seqid=A1SKF7

Min size:
http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=up&seqid=A0MFH8
Median size:
http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=ja;seqid=gi%7C89056127%7Cref%7CYP_511578.1%7C
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=ob&seqid=ENSOGAP00000000621
Max size:
http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=mm&seqid=ENSMUSP00000054275

Script 2: scop.cgi	Calls/s: 0.133	Throughput: 69.51k/s
	    pct	    total	min	    max	    avg	    95%	    stddev	median
Calls	31.75	11462
Time	14.12	2123.07	0.12	2.23	0.19	0.44	0.25	0.15
Size	14.58	144.11M	7.34k	179.33k	12.87k	19.59k	5.41k	12.16k
Time range [07/Sep/2009:00:00:01 +0100] to [07/Sep/2009:23:59:53 +0100]

Min time:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=151351
Median time:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=20876
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=27844
Max time:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=153375

Min size:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=47094
Median size:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=139890
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=24136
Max size:
http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=53931


Script 3: model.cgi	Calls/s: 0.021	Throughput: 38.14k/s
	    pct	    total	min	    max	    avg	    95%	    stddev	median
Calls	5.06	1826
Time	2.73	410.30	0.11	4.10	0.22	0.67	0.30	0.17
Size	1.55	15.28M	7.74k	9.18k	8.57k	8.95k	965.55	8.78k
Time range [07/Sep/2009:00:00:08 +0100] to [07/Sep/2009:23:59:19 +0100]

Min time:
http://supfam.org/SUPERFAMILY/cgi-bin/model.cgi?model=0045128
Median time:
http://supfam.org/SUPERFAMILY/cgi-bin/model.cgi?model=0053405
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/model.cgi?model=0036357
Max time:
http://supfam.org/SUPERFAMILY/cgi-bin/model.cgi?model=0039267

Min size:
http://supfam.org/SUPERFAMILY/cgi-bin/model.cgi?model=0036517
Median size:
http://supfam.org/SUPERFAMILY/cgi-bin/model.cgi?model=0053155
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/model.cgi?model=0045171
Max size:
http://supfam.org/SUPERFAMILY/cgi-bin/model.cgi?model=0037989


Script 4: gen_list.cgi	Calls/s: 0.017	Throughput: 1.24M/s
	    pct	    total	min	    max	    avg	    95%	    stddev	median
Calls	4.04	1458
Time	2.56	385.37	0.14	1.72	0.26	0.59	0.31	0.22
Size	48.18	476.34M	49.61k	545.68k	334.55k	504.07k	92.32k	330.93k
Time range [07/Sep/2009:00:06:09 +0100] to [07/Sep/2009:23:59:49 +0100]

Min time:
http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?genome=hu
Median time:
http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?genome=ce
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?genome=67
Max time:
http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?genome=k4

Min size:
http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?listtype=fa;genome=5s;sortby=prot
Median size:
http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?genome=d2
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?genome=of
Max size:
http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?password=


Script 5: taxonomic_gen_list.cgi	Calls/s: 0.004	Throughput: 650.07k/s
	    pct	    total	min	    max	    avg	    95%	    stddev	median
Calls	0.86	310
Time	0.98	147.65	0.39	1.01	0.48	0.71	0.49	0.45
Size	9.48	93.73M	309.62k	309.62k	309.62k	309.62k	0	309.62k
Time range [07/Sep/2009:00:11:59 +0100] to [07/Sep/2009:23:58:48 +0100]

Min time:
http://supfam.org/SUPERFAMILY/cgi-bin/taxonomic_gen_list.cgi
Median time:
http://supfam.org/SUPERFAMILY/cgi-bin/taxonomic_gen_list.cgi
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/taxonomic_gen_list.cgi
Max time:
http://supfam.org/SUPERFAMILY/cgi-bin/taxonomic_gen_list.cgi

Min size:
http://supfam.org/SUPERFAMILY/cgi-bin/taxonomic_gen_list.cgi
Median size:
http://supfam.org/SUPERFAMILY/cgi-bin/taxonomic_gen_list.cgi
95th percentile:
http://supfam.org/SUPERFAMILY/cgi-bin/taxonomic_gen_list.cgi
Max size:
http://supfam.org/SUPERFAMILY/cgi-bin/taxonomic_gen_list.cgi


Most frequently requested URLs:
 310	http://supfam.org/SUPERFAMILY/cgi-bin/taxonomic_gen_list.cgi
  20	http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=46458
  12	http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi
  12	http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi
   8	http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=0
   8	http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?genome=2k
   7	http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=46966
   7	http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=hs;seqid=ENSP00000222956
   7	http://supfam.org/SUPERFAMILY/cgi-bin/scop.cgi?sunid=52934
   6	http://supfam.org/SUPERFAMILY/cgi-bin/gen_list.cgi?genome=0q
   6	http://supfam.org/SUPERFAMILY/cgi-bin/gene.cgi?genome=up&seqid=Q0PQ90
~~~~


# Installation and configuration

How to install and configure the apache-response-time command.

## System requirements

 * Unix like operating system
 * perl 5.8 or higher
 * working apache web server installation


## Installation

In 2 commands:

~~~~
wget https://raw.githubusercontent.com/makeyourownmaker/apache-response-time/master/apache-response-time
chmod u+x apache-response-time
~~~~

## Testing

Verify the command works:

~~~~
./apache-response-time -h
~~~~


## Apache configuration

By default the apache log format does not include the response time 
directive, which apache-response-time depends on.

Edit your apache configuration file to enable the response time directive (*%D*):

~~~~
#LogFormat "%h %l %u %t \"%r\" %>s %b"    # Default LogFormat
LogFormat "%h %l %u %t \"%r\" %>s %b %D"  # LogFormat including response time
~~~~

Restart apache.

[Apache LogFormat directive.](http://httpd.apache.org/docs/2.0/mod/mod_log_config.html#logformat)

# Command line options


The command line prompt is indicated by the *$* symbol.

List command line options with explanation:

~~~~
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


~~~~


# Usage examples


## Rank scripts by average response time per call

~~~~
apache-response-time -o call_time
~~~~


## Show top 25 scripts

~~~~
apache-response-time -l 25
~~~~


## Performance analysis for 6th June

~~~~
apache-response-time -d 06/Jun/2009
~~~~


## Python scripts under PeoplesFrontJudea directory on brian.com domain

~~~~
apache-response-time -e py -b PeoplesFrontJudea -s http://brian.com
~~~~



