About
=====

stravacmd is a Python command line tool for interfacing with
[Strava](https://www.strava.com).  It uses
[pystrava](https://github.com/j2sol/pystrava) to communicate with the Strava
API.

To run directly from a checkout, clone pystrava in another directory and link pystrava/src/pystrava to src/pystrava within stravacmd.

Usage
=====

stravacmd has a help output and help output for each target:

    $ ./stravacmd --help
    usage: stravacmd [-h] [-v] [-q] {rides} ...

    optional arguments:
      -h, --help  show this help message and exit
      -v          verbose
      -q          show no extra output

    Targets:
      Valid commands

      {rides}
        rides     Work with Strava rides

    $ ./stravacmd rides --help
    usage: stravacmd rides [-h] --athlete ATHLETE [--club CLUBID]
                           [--startdate STARTDATE] [--enddate ENDDATE]
                           [--start STARTID] [--backup BACKUP]

    Display strava rides

    optional arguments:
      -h, --help            show this help message and exit
      --athlete ATHLETE     List rides for a particular athlete
      --club CLUBID         List rides for a particular club
      --startdate STARTDATE
                            List rides starting from YYYY-MM-DD
      --enddate ENDDATE     List rides until YYYY-MM-DD
      --start STARTID       List rides newer than (including) this ride number
      --backup BACKUP       Backup the rides found to the path provided. Ride file
                            names will be <id>.tcx and existing rides will not be
                            overwritten.

Examples
=====

    $ ./stravacmd rides --athlete 279921 --enddate 2011-11-27
    4232472 11/20/2011 Parkland, WA
    4232479 11/13/2011 Seattle, WA
    4232476 11/06/2011 Lakewood, WA
    4232478 11/04/2011 Tacoma, WA
    4232480 09/19/2011 Tacoma, WA

    $ ./stravacmd rides --athlete 279921 --startdate 2013-02-10 --enddate 2013-02-14
    41019628 Dash Point BP
    40786069 School + coffee shop

    $ ./stravacmd rides --athlete 279921 --startdate 2013-01-01 --backup output/
    Wrote /Users/jkeating/src/stravacmd/src/output/41019628.tcx
    Wrote /Users/jkeating/src/stravacmd/src/output/40786069.tcx
    Wrote /Users/jkeating/src/stravacmd/src/output/40366287.tcx


