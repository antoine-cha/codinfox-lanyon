---
layout: post
title: argparse-print-defaults.md
author: Antoine
tags: [Antoine,python]
---
## Printing default values with argparse

### Normal mode

- code (`visu.py`):
```Python
parser = argparse.ArgumentParser(description="View the live in your web browser")    
                           
parser.add_argument('--config',                                                         
                    help='config.ini file of the run',                                  
                    required=False,                                                     
                    default='../config.ini')                                            
parser.add_argument('--port',                                                           
                    help='specify port to run server',                                  
                    required=False,                                                     
                    default=5000,                                                       
                    type=int)                                                           
parser.add_argument('-r', '--reload',                                                   
                    help='Description',                                                 
                    action='store_true')                                                
args = parser.parse_args()                                                              
```
- Using the script:
```Shell
$ python visu.py --help

usage: visualisator.py [-h] [--config CONFIG] [--port PORT] [-r]

View the live in your web browser

optional arguments:
  -h, --help       show this help message and exit
  --config CONFIG  config.ini file of the run
  --port PORT      specify port to run server
  -r, --reload     Description
```

### Using ArgumentDefaultsHelpFormatter

- Change the first line of `visu.py` to:
```Python
parser = argparse.ArgumentParser(description="View the live in your web browser",       
                                 formatter_class=argparse.ArgumentDefaultsHelpFormatter)
```
- Using the script:
```Shell
$ python visu.py --help

usage: visualisator.py [-h] [--config CONFIG] [--port PORT] [-r]

View the live in your web browser

optional arguments:
  -h, --help       show this help message and exit
  --config CONFIG  config.ini file of the run (default: ../config.ini)
  --port PORT      specify port to run server (default: 5000)
  -r, --reload     Description (default: False)
```
