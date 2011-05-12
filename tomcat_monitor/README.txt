monitors tomcat access log gathering: 
	throughput requests per minute (rpm),  response time (rt),
	top 5 requests
	
Requires specific access log format:
pattern='%h %l %u %t %D "%r" %s %b"'

	•	%h - Remote host name (or IP address if resolveHosts is false)
	•	%l - Remote logical username from identd (always returns '-')
	•	%u - Remote user that was authenticated (if any), else '-'
	•	%t - Date and time, in Common Log Format
	•	%D - Time taken to process the request, in millis
	•	%r - First line of the request (method and request URI)
	•	%S - User session ID
	•	%b - Bytes sent, excluding HTTP headers, or '-' if zero

which looks like:
	72.11.70.114 - - [18/Apr/2011:22:34:35 +0000] 40 "GET /client/editEmployee.jsp HTTP/1.1" 200 28500"

Update AccessLogValve in jboss-web.deployer/server.xml to:
	<Valve className="org.apache.catalina.valves.AccessLogValve"
    	prefix="localhost_access_log." suffix=".log"
    	pattern='%h %l %u %t %D "%r" %s %b"' directory="${jboss.server.home.dir}/log" 
    	resolveHosts="false" />
