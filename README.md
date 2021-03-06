ipstats
=======

High Performance per IP address (and protocol) bandwidth statistics supporting IPv4 & IPv6 addressing.

# Example Output
```
#DIRECTION IP TCP UDP GRE IPIP ICMP IPSEC OTHER
IN 1.2.3.4 100 5552 0 0 0 0 0 0 0 0 0 0
OUT 1.2.3.4 0 0 0 0 0 0 0 0 0 0 0 0
```

IP ```1.2.3.4``` has sent no traffic, however it has received 100 TCP packets, totalling 5552 bytes. Counters are implemented using a 32 bit unsigned integer for packets and bytes bytes.

# Usage
```ipstats [device]```

ipstats listens on a given device. ```all``` can be specified to listen to all interfaces.

# Installation
ipstats can be compiled using the included ```make.sh```. PF_RING support can be enabled by adding using ```make.sh pf_ring```. A helper script to compile and install pf_ring has been included (see contrib)

# Performance
Scales linearly to a large number of IP addresses and PPS. Compiling and using PF_RING is strongly recommended. On a reasonable Xeon the CPU usage is minimal (at 30mbit). CPU As measured on a Intel(R) Atom(TM) CPU D525 @ 1.80GHz:

 * __libpcap 1.0+:__ ~10% CPU usage at 20mbit
 * __pf_ring:__ <0.5% CPU usage at 20mbit