speedtest-cli
=============

Command line interface for testing internet bandwidth using
speedtest.net

**This version is forked from https://github.com/sivel/speedtest-cli - I've added --json, which outputs the results as a JSON object (for further processing) and suppresses all other output.**

Versions
--------

speedtest-cli works with Python 2.4-3.4

Installation
------------

pip / easy\_install
~~~~~~~~~~~~~~~~~~~

::

    pip install speedtest-cli

or

::

    easy_install speedtest-cli

Github
~~~~~~

::

    pip install git+https://github.com/dermotw/speedtest-cli.git

or

::

    git clone https://github.com/dermotw/speedtest-cli.git
    python speedtest-cli/setup.py install

Just download (Like the way it used to be)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    wget -O speedtest-cli https://raw.githubusercontent.com/dermotw/speedtest-cli/master/speedtest_cli.py
    chmod +x speedtest-cli

or

::

    curl -Lo speedtest-cli https://raw.githubusercontent.com/dermotw/speedtest-cli/master/speedtest_cli.py
    chmod +x speedtest-cli

Usage
-----

::

    $ speedtest-cli -h
    usage: speedtest-cli [-h] [--bytes] [--share] [--simple] [--list]
                         [--server SERVER] [--mini MINI] [--source SOURCE]
                         [--timeout TIMEOUT] [--secure] [--version]

    Command line interface for testing internet bandwidth using speedtest.net.
    --------------------------------------------------------------------------
    https://github.com/dermotw/speedtest-cli

    optional arguments:
      -h, --help         show this help message and exit
      --bytes            Display values in bytes instead of bits. Does not affect
                         the image generated by --share
      --share            Generate and provide a URL to the speedtest.net share
                         results image
      --simple           Suppress verbose output, only show basic information
      --json             Output results as a JSON object
      --list             Display a list of speedtest.net servers sorted by
                         distance
      --server SERVER    Specify a server ID to test against
      --mini MINI        URL of the Speedtest Mini server
      --source SOURCE    Source IP address to bind to
      --timeout TIMEOUT  HTTP timeout in seconds. Default 10
      --secure           Use HTTPS instead of HTTP when communicating with
                         speedtest.net operated servers
      --version          Show the version number and exit

Inconsistency
-------------

It is not a goal of this application to be a reliable latency reporting tool.

Latency reported by this tool should not be relied on as a value indicative of ICMP
style latency. It is a relative value used for determining the lowest latency server
for performing the actual speed test against.

There is the potential for this tool to report results inconsistent with Speedtest.net.
There are several concepts to be aware of that factor into the potential inconsistency:

1. Speedtest.net has migrated to using pure socket tests instead of HTTP based tests
2. This application is written in Python
3. Different versions of Python will execute certain parts of the code faster than others
4. CPU and Memory capacity and speed will play a large part in inconsistency between
   Speedtest.net and even other machines on the same network

Issues relating to inconsistencies will be closed as wontfix and without
additional reason or context.
