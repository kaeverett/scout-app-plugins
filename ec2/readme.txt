When talking a local systems guru, Dave Liddell, he suggested I monitor my EC2 resources a little more closely.  Using AWS EC2 is still just shared hosting.
This plugin allows you to monitor:
 - steal time: CPUs while the hypervisor was servicing another virtual processor
 - ping time
 - EBS performance


Suggested thresholds:
 Not sure yet, but I will update after I have more data.  Here's where I'm starting.
 - ping times above 75ms
 - steal consistently above 20%

 Reading http://www.igvita.com/2009/06/23/measuring-optimizing-io-performance they suggest:
 - await and svctime above 50ms
 - average queue size above 9

