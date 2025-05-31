# Poxy-Chains
Set up process for running proxy-chains on ubuntu with added security.


Sooo.... I watched this video by David Bombal,


VIDEO > https://www.youtube.com/watch?v=LEbAxsYRMcQ


It's a video on setting up and using Poxy-chains on kali?


Difference is im using Ubuntu. So non of this is installed by default why not share my process. P.S Im obsessed with debian based OS refuse to use anything else. 


proxychains:


Its linux so to be able to edit configuratiions your just accessing a file. super easy. 


sudo apt install proxychains


You can locate the configuration file here but its not neccessary because protocols, subnet, and ports are set by default.


sudo mousepad /etc/proxychains.conf


Defaults: 


Socks4 protocol 


127.0.0.1 subnet 


9050 is the unofficial but official port for Tor


socks4 127.0.0.1 9050


There is also a variable for number of nodes/hops in the chain,


chain_len = 3


WERE NOT RUNNING PROXY-CHAIN YET. 


We need to download tor, not tor browser:


sudo apt update


sudo apt install apt-transport-https curl gnupg


# Import the Tor Project's GPG key
wget -qO- https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --dearmor | sudo tee /usr/share/keyrings/torproject-archive-keyring.gpg >/dev/null


# Add the Tor repository to sources.list.d
echo "deb [signed-by=/usr/share/keyrings/torproject-archive-keyring.gpg] https://deb.torproject.org/torproject.org $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/tor.list


# Update package list
sudo apt update


# Install Tor
sudo apt install tor


Okay so far so good, next up we need to install annonsurf, 

Anonsurf by Und3rf10w:

"Anonsurf anonymizes your entire system's network traffic by routing it through the Tor network. "


sudo apt install git


sudo git clone https://github.com/Und3rf10w/kali-anonsurf 


lets see where it's at,


ls -l 


cd ~/kali-anonsurf


ls -l will list file and folders in the current directory, we cd into the kali-anonsurf folder. inside we can run,


sudo ./installer.sh


(a few moments later)


when you run anonsurf you'll get a promp that says,



killing dangerous applications
cleaning dangerous cache elements
stoping ipv6 services:


starting annon mode


saved iptables rules


modified resolv.conf to use tor and private internet...


you are under annonSurf tunnel

To run this you type 



I wanted a secure browser without running Tor, so here is the process for installing brave.


Release Channel Installation
Debian, Ubuntu, Mint


sudo apt install curl


sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg


echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list


sudo apt update


sudo apt install brave-browser


Oookay there are options for using more hardend operating system but were not trying to hide from NSA or cyber gangs this is just to protect use from commercial industries. ESENTIALLY ELIMINATING THE NEED FOR A VPN. 


Now that all this is installed we just run these three commands and enter are password when requested,


TO RUN:

sudo anonsurf start

systemctl start tor

proxychains brave-browser

when you close the browser and want to stop Proxy/Tor,

RUN:

systemctl stop tor

systemctl anonsurf stop



THERE IS SO MUCH MORE INFO IN THIS VIDEO ON OSINT AND FORENSICS SO IF YOU WANT MORE INFORMATION WATCH THE VIDEO.
