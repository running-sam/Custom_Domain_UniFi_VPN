## Custom Domain UniFi VPN
Using custom domain for UniFi VPN

1)	Register for Free Cloudflare account, https://www.cloudflare.com/plans/
2)	Once registered add a site, “add a site”
3)	It will ask for your domain “My_Domain.com" it will then provide you with two DNS entries to add to your hosting provider, this will then mean that Cloudflare will manage your DNS entires.  Personally worth it as Cloudflare is quick and has lots of features.  

Once Cloudflare is managing your domains go to your domain, then DNS.

4)	Add a A record for what ever you want your VPN address to be “vpn.mjdix.ch" put the IP address as “172.1.1.1” (place holder).  

5)	Go to https://www.dnsomatic.com register for an account, then add a service, “Cloudflare” 

Email is the email you used to setup cloudflare,
API Token is the cloudflare “Global API Key” on the overview page for your domain on the right hand side towards the bottom, click get your API token.  
Hostname is the new “A” record i.e. “something.MY_Domain.com"
Domain is your domain “My_Domain"
Then “update account info”

6)	Then on UDM Pro, “settings” - “Internet” - “Primary Internet” (or which ever you want” - “Dynamic DNS” - “Create New Dynamic DNS”
Service - dnsomatic
Hostname - all.dnsomatic.com
Username - [the user name on DNSoMATIC]
Password - [Password for DNSoMATIC]
Server - updates.dnsomatic.com/nic/update?hostname=%h&myip=%i
Save,

You can then look at DNSoMATIC refresh the page you should see your IP updated, if you then go to Cloudflare and refresh your DNS records you will notice the place holder is now your public ip.  

On the UDM Pro, go - VPN - VPN Server - 10CH “WireGuard” - “Use alternative address for clients” add your new domain “something.My_Domain.com"

When you download the config files for clients this new domain will then be in place of the IP in the config.  I would suggest updating the “Allowed IP’s” in the config files to be “0.0.0.0/0” this will send all traffic over the VPN.  

