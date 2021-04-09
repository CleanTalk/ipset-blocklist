# ipset-blocklist
A shell application to implement CleanTalk blacklists with iptables on a Linux server.
CleanTalk provides access to the spam IPs database. You can use the IPset format to automatically update data in your Iptables or FirewallD firewall.

You can see how to connect CleanTalk IPSet to Iptables here https://cleantalk.org/help/iptables-connect

The spam IP address database is updated once an hour. IP addresses get into the database only if they were marked as spam on several websites in a short time, which significantly reduces the risk of false positives.

All spam IP and Email addresses in files are distributed depending on their spam activity.

Offline Database. Around 10,000 IPs daily. Spam records with frequency> = 200
Offline Database. Around 13,000 IPs daily. Spam records with frequency> = 150
Offline Database. Around 19,000 IPs daily. Spam records with frequency> = 100
Offline Database. Around 76,000 IPs. All spam records.

frequency - is the number of websites on which the IP was seen as spam.

You can download a database of blacklists of IP and Email addresses in two formats CSV and IPSet or use the API.

You can find out more about the spam IP address database and the dynamics of records update here https://cleantalk.org/blacklists 
