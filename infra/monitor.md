# Monitoring

## Process Monitoring
Process monitoring at a glance can be a time saver while the CTF is live. Being able to, at a glace, identify if a problem is running or not can help pinpoint possible outages and lead to getting the problem online more quickly. Having this for every problem (and potentially critical network components) in a single page is a nice "not my fault" board to have, narrowing possible problems individual exploits and allowing time to be dedicated to other issues. The current tool of choice is Monit, which presents a web dashboard with the status of the desired services, meaning every challenge can be easily seen running at any point in time.

## Why Monit?
Monit is extremely lightweight. It requires no back end database, minimal overhead, and as a general statement, just works. It can monitor processes via their process id (which you have been handily given by runit, right?) and monitor web assets via a persistent ping to insure they are online. Further, each process can be monitored with a single line of configuration.

	CHECK PROCESS <unique name> <PIDFILE <path> | MATCHING <regex>>

In Void Linux, the path to the PIDFILE will be `/var/service/{{ service_name }}/supervise/pid`. With all of the challenges monitored with Monit, it is easy to pull up the web-page and confirm all challenges are up, making it possible to easily detect outages before reports even come it. If nothing else, Monit is great at relieving stress, as it instills confidence in the fact the CTF is not experiencing an outage, at least from the exploitable challenges side.
