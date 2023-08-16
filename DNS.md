# keenable
<aside>
💡

To set up a DNS server using the BIND9 image you've mentioned and configure it to serve the "[keenable.in](http://keenable.in/)" domain, follow these steps:

1. **Configure DNS Server Container:**
Start by accessing the container's shell:
    
    ```bash
    podman exec -it dns-server /bin/bash
    
    ```
    
    Once inside the container, you'll need to modify BIND9's configuration files.
    
2. **Edit BIND9 Configuration:**
The main configuration file for BIND9 is usually located at `/etc/bind/named.conf`. Edit this file using a text editor (e.g., `nano`, `vim`, `emacs`):
    
    ```bash
    nano /etc/bind/named.conf
    
    ```
    
3. **Add Zone Configuration:**
Inside `named.conf`, you'll need to add a new zone configuration for your "[keenable.in](http://keenable.in/)" domain. Add the following lines to the end of the file:
    
    ```
    zone "keenable.in" {
        type master;
        file "/etc/bind/keenable.in.zone";  # Path to zone file
    };
    
    ```
    
4. **Create Zone File:**
Create the zone file at the specified path (`/etc/bind/keenable.in.zone` in this case):
    
    ```bash
    nano /etc/bind/keenable.in.zone
    
    ```
    
    Add the following content to the zone file to define DNS records for your domain:
    
    ```
    $TTL 1D
    @       IN      SOA     ns.keenable.in. admin.keenable.in. (
                                2023081001 ; serial
                                8H ; refresh
                                2H ; retry
                                4W ; expire
                                1D ; minimum
                                )
    
    @       IN      NS      ns.keenable.in.
    @       IN      A       192.168.1.33
    ns      IN      A       192.168.1.33
    
    ```
    
5. **Restart BIND9:**
Exit the container shell and restart the BIND9 service:
    
    ```bash
    exit
    podman restart dns-server
    
    ```
    
6. **Configure Local Resolvers:**
On your local machine or devices, update the DNS resolver settings to use your newly created DNS server (192.168.1.33) for the "[keenable.in](http://keenable.in/)" domain. You can typically do this in your network settings.
7. **Test DNS Resolution:**
Test whether the DNS server is working as expected:
    
    ```bash
    nslookup keenable.in 192.168.1.33
    
    ```
    

Remember that setting up and configuring DNS involves more than just these steps, especially in production environments. This is a basic setup for educational purposes. You might need to adjust firewall settings, DNSSEC, security configurations, and other factors for a production-ready DNS server.

</aside>
