# ipset-blocklist
A shell application to implement CleanTalk blacklists with iptables on a Linux server.

If you want to use our IP spam database for IPtables you need to do the following:

1. Install IPset packet. 

For Debian: apt-get  install ipset

For Redhat: yum install ipset  -y

2. Check if you have a CURL with SFTP support installed:

curl -V | grep sftp -o

Download missing libraries.

3. Download CleanTalk scripts.

4. Make a folder for the .conf file and lists:

mkdir -p /etc/ipset-blacklist

and copy ipset-blacklist.conf file from downloaded archive to this fodder.

5. Copy update-blacklist.sh file from downloaded archive to /usr/local/sbin.

Make it executable: chmod +x /usr/local/sbin/update-blacklist.sh

6. Enter your SFTP credentials to ipset-blacklist.conf.
7. . Run the script:

/usr/local/sbin/update-blacklist.sh /etc/ipset-blacklist/ipset-blacklist.conf

The script creates a list for IPtables: ip-blacklist.restore 

8. To connect the list run:

ipset restore < /etc/ipset-blacklist/ip-blacklist.restore

iptables -I INPUT 1 -m set --match-set blacklist src -j DROP

9. For automatic updates please add to cron these lines:

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

MAILTO=root

33 23 * * *     root /usr/local/sbin/update-blacklist.sh /etc/ipset-blacklist/ipset-blacklist.conf

 

You can check the results:

iptables -L INPUT -v --line-numbers
