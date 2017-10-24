---
layout: post
title: Beautiful logging in Python
author: Antoine
tags: [python]
---

## The `logging` module

[Documentation](https://docs.python.org/2/library/logging.html)

This module is extremely useful and has many unknown features.

## Useful features (to be completed)

### LogRecord attributes

- Every message from the message is an object of type `LogRecord`. 
- This gives us access to very useful information, here are some of them:

Name | Format | Description
---- | ------ | ---------
asctime | %(asctime)s |	Human-readable time when the LogRecord was created. By default this is of the form ‘2003-07-08 16:49:45,896’ (the numbers after the comma are millisecond portion of the time).
levelname | `%(levelname)s` | Text logging level for the message ('DEBUG', 'INFO', 'WARNING', 'ERROR', 'CRITICAL').
filename | `%(filename)s` | Filename portion of pathname.
lineno | `%(lineno)d` | Source line number where the logging call was issued (if available).

Source: [LogRecord-attributes](https://docs.python.org/2/library/logging.html#logrecord-attributes)

## Defining loggers from `yaml` file

Instead of going through a long list of calls to the `logging` API, configuring your logger can be done from files.

### YAML example
- `logging_conf.yaml`
```yaml
version: 1                                                                               
disable_existing_loggers: False                                                          
formatters:                                                                              
    simple:                                                                              
        format: "[%(asctime)s]%(name)s %(levelname)s(%(module)s %(lineno)d): %(message)s"
        datefmt: "%Z %Y-%m-%d %H:%M:%S"                                                  
                                                                                         
handlers:                                                                                
    console:                                                                             
        class: logging.StreamHandler                                                     
        level: INFO                                                                      
        formatter: simple                                                                
        stream: ext://sys.stdout                                                         
                                                                                         
loggers:                                                                                 
    prefetch:                                                                            
        level: INFO                                                                      
        handlers: [console]                                                              
        propagate: no                                                                    
```
- `main.py`
```Python
import pyyaml
import logging
import logging.config
with open("logging_conf.yaml") as f:                   
    logging.config.dictConfig(yaml.safe_load(f.read()))
LOGGER = logging.getLogger("my-logger")                 
```
