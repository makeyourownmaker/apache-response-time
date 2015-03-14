# System requirements #

  * Unix like operating system
  * perl 5.8 or higher
  * working apache web server installation

# Installation #

In 2 commands:
```
   wget http://apache-response-time.googlecode.com/files/apache-response-time.gz
   gunzip apache-response-time.gz
```

# Testing #

Verify the command works:
```
   ./apache-response-time -h
```


# Apache configuration #

By default the apache log format does not include the response time directive, which apache-response-time depends on.


Edit your apache configuration file to enable the response time directive (**%D**):
```
#LogFormat "%h %l %u %t \"%r\" %>s %b"    # Default LogFormat
LogFormat "%h %l %u %t \"%r\" %>s %b %D"  # LogFormat including response time
```

Restart apache.

## See also ##

[Usage examples](Usage.md).

[Apache LogFormat directive](http://httpd.apache.org/docs/2.0/mod/mod_log_config.html#logformat).