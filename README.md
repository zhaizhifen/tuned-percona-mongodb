# tuned-percona-mongodb
A performance-focused [tuned](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Power_Management_Guide/Tuned.html) profile for MongoDB on CentOS/Redhat Linux.

## About
The profile sets various recommended settings for a production mongodb deployment (*sysctls, io scheduler, THP, CPU states, etc*). Tested on CentOS/Redhat 7 although it *may* work on Debian's tuned in 8+.

Many of the tunings are justified/explained in this blog post: https://www.percona.com/blog/2016/08/12/tuning-linux-for-mongodb/

### Experimental
While this profile has undergone testing, it comes with no gurantees and it is possible these tunings will not work well for your situation.

### Why?
Tuned's daemon runs by default on CentOS/Redhat hosts since version 7, managing the tunings of operating system via profiles. Tuning the system manually outside of using tuned profiles will often cause your settings to be overriden by tuned itself or future upgrades. Tuned profiles abstract the details of where/how to apply tunings in a consolidated, easy-to-troubleshoot location.

## Install
*Note: The profile assumes /dev/sda is an Linux "os" disk and /dev/sdX are for database data. Adjust "devices=" in the disk section if this is not the case.*

```
$ git clone https://github.com/Percona-Lab/tuned-percona-mongodb
$ cd tuned-percona-mongodb
$ sudo make enable
```

## Uninstall
*Note: uninstall step enables the 'latency-performance' profile, change after if needed*
```
$ cd /your/git/path/tuned-percona-mongodb
$ sudo make uninstall
```

## Contact
- Tim Vaillancourt - [Github](https://github.com/timvaillancourt), [Email](mailto:tim.vaillancourt@percona.com)
- Percona - [Twitter](https://twitter.com/Percona) / [Contact Page](https://www.percona.com/about-percona/contact)
