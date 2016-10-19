# Pen
Light  "[pen]( http://siag.nu/pen/) 0.33.2" in [alpine](/r/_/alpine/) only 6.6 MB [Dockerfile](https://github.com/themonnie/docker-pen/blob/master/Dockerfile)

Howto: http://siag.nu/pen/ 



## Docker use
```bash
docker run -d -p 443:443 themonnie/pen 0.0.0.0:443 web0:443 web1:443
```

## Docker-compose use

```docker-compose
...
pen-amqp:
  image: galexrt/pen:latest
  hostname: pen
  ports: 
    - 5672:5672
  links:
    - rabbitmq0
    - rabbitmq1
  command: "-d pen:5672 rabbitmq0:5672 rabbitmq1:5672"
...
```
## pen usage
```
usage:
  pen [-C addr:port] [-X] [-b sec] [-c N] [-e host[:port]] \
	  [-t sec] [-x N] [-w dir] [-UHPWadfhrs] \
          [-o option] \
	  [host:]port h1[:p1[:maxc1[:hard1[:weight1[:prio1]]]]] [h2[:p2[:maxc2[:hard2[:weight2[:prio2]]]]]] ...

  -B host:port abuse server for naughty clients
  -C port   control port
  -T sec    tracking time in seconds (0 = forever) [0]
  -H	add X-Forwarded-For header in http requests
  -U	use udp protocol support
  -N	use hash for initial server selection without save server
  -O option	use option in penctl format
  -P	use poll() rather than select()
  -Q    use kqueue to manage events (BSD)
  -W    use weight for server selection
  -X	enable 'exit' command for control port
  -a	debugging dumps in ascii format
  -b sec    blacklist time in seconds [30]
  -c N      max number of clients [2048]
  -d	debugging on (repeat -d for more)
  -e host:port emergency server of last resort
  -f	stay in foregound
  -h	use hash for initial server selection
  -j dir    run in chroot
  -F file   name of configuration file
  -l file   logging on
  -r	bypass client tracking in server selection
  -s	stubborn selection, i.e. don't fail over
  -t sec    connect timeout in seconds [3]
  -u user   run as alternative user
  -p file   write pid to file
  -x N      max number of simultaneous connections [500]
  -w file   save statistics in HTML format in a file
  -o option use option in penctl format

example:
  pen smtp mailhost1:smtp mailhost2:25 mailhost3
```
