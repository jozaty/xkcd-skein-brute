#Brute-forcer for [XKCD](http://almamater.xkcd.com/)

This should comile on any POSIX-compliant system, and has been tested on Mac OS X 10.8 (Mountain Lion) and CentOS release 5.9 (Final).

##Instructions (POSIX Systems)
1. Download archive from [here](https://github.com/yasyf/xkcd-skein-brute/archive/master.zip)
2. Make sure to have [Python 3](http://www.python.org/download/) installed (`apt-get install python3`,`brew install python3` or similar should work)
3. Extract and `cd` into the master directory
4. Run the following:

```
make
./screen-nice-wrapper.sh
```

##Information

The problem is basically hashing large swaths of key space to find
near-collisions with a given bitstring. The better the 'near-ness', the higher
your rank. It is computed by taking the bitwise distance from the hash of the
input string to the given bitstring.

An ideal solver would be an implementation of the inverse skein function. Hah.

See main.c.

Skein block performance:

With GCC -O3 on this Core i7 machine, the C implementation yields:

    Trial 0 Skeins/sec: 667672.35
    Trial 1 Skeins/sec: 677591.17
    Trial 2 Skeins/sec: 693625.83
    Trial 3 Skeins/sec: 703415.01
    Trial 4 Skeins/sec: 660963.22

With the assembly implementation:

    Trial 0 Skeins/sec: 933069.85
    Trial 1 Skeins/sec: 1338020.03
    Trial 2 Skeins/sec: 996060.88
    Trial 3 Skeins/sec: 1022662.78
    Trial 4 Skeins/sec: 1141148.95

Unfortunately, the hashes produced by the assembly implementation seem
incorrect. =(

##Credits
Forked from @uakfdotb's https://github.com/uakfdotb/xkcd-skein-brute.