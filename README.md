#It will works under **Centos 7** for clients op. system and Puppet Enterprise 2015.3.2 edition for Puppet server. On the Centos 7 client you **must enabled the epel repo**, because it need for nginx install! I looking for golang installer and nginx installer at puppetforge, but I can't find perfect solution for me, that's why I write 2 module for solve the problems :)

##**INSTALL:**
- Create a directory on Puppet server a directory to clone this git repo
- cd yourcreateddirectory
- git clone https://github.com/koqsz/automatpupp.git
- cd automatpupp
- cp puppet-modules.tar.gz /etc/puppetlabs/code/environments/production/modules
- cd /etc/puppetlabs/code/environments/production/modules
- tar -xzf puppet-modules.tar.gz  <-- You will see 2 directory **( kcs-goinstall, kcs-lbinstall )**
- **Write the correct IP address of your webservers to the ./kcs-lbinstall/files/lb.conf!!!**
- Open the Puppet Server webpage.
- Create 2 node groups ( the groups names is your choises! )
- The group which has been created for load balancer push 1 Centos client. In the **Classes** section add the **lbinstall** class. **You must leave empty the parameter section!** 
- The group which has been created for webservers push 2 Centos client. In the **Classes** section add the **goinstall** class. **You must leave empty the parameter section!**
- On the 3 computer run the Puppet and it will be install the nginx server and configuration on load balancer server and install the go language envinronment and copy the files for webservers!

The nginx and the go test file will run automatically!!

##*TEST*##
- Open a webbrowser
- http://ipaddressofloadbalancer
- push refresh button ( once the first webserver hostname you will see, after refresh the second webserver hostname you will see)

If you shutdown one of the webserver you will see only the other webserver hostname on the webpage!


