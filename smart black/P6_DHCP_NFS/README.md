<body>

<h1>Server Side DHCP Configuration</h1>

<pre><code>sudo apt-get install isc-dhcp-server</code></pre>
<pre><code>sudo nano /etc/default/isc-dhcp-server</code></pre>
<p>- INTERFACES="ens33"</p>

<pre><code>sudo nano /etc/dhcp/dhcpd.conf</code></pre>
<p>- <code>#option domain-name "example.org";</code></p>
<p>- <code>#option domain-name-servers ns1.example.org, ns2.example.org;</code></p>
<p>- <code>authoritative</code> (Uncomment this line)</p>
<pre><code>subnet 192.168.182.0 netmask 255.255.255.0 {
    range 192.168.182.100 192.168.182.200;
    #option domain-name-servers ns1.internal.example.org;
    #option domain-name "internal.example.org";
    option subnet-mask 255.255.255.0;
    option routers 192.168.182.255;
    option broadcast-address 192.168.182.255;
    default-lease-time 600;
    max-lease-time 7200;
}</code></pre>

<pre><code>sudo systemctl start isc-dhcp-server</code></pre>
<pre><code>sudo systemctl status isc-dhcp-server</code></pre>
<pre><code>sudo systemctl enable isc-dhcp-server</code></pre>

<h1>Client Side Configuration</h1>
<pre><code>sudo nano /etc/network/interfaces</code></pre>
<p><code>auto lo</code></p>
<p><code>iface lo inet loopback</code></p>
<p><code>auto ens33</code></p>
<p><code>iface ens33 inet dhcp</code></p>

<pre><code>ip a</code></pre>
<pre><code>sudo systemctl restart networking</code></pre>

<h1>Server Side to Check Connection</h1>
<pre><code>sudo nano /var/lib/dhcp/dhcpd.leases</code></pre>

<h1>Configure NFS Server</h1>
<pre><code>sudo apt-get install nfs-kernel-server</code></pre>
<h4>Create folder which you want to share over network and assign permissions</h4>
<pre><code>sudo mkdir /public</code></pre>
<pre><code>sudo mkdir /private</code></pre>
<pre><code>sudo chmod 755 /public</code></pre>
<pre><code>sudo chmod 777 /private</code></pre>
<h4>Configure /etc/exports</h4>
<pre><code>sudo nano /etc/exports</code></pre>
<p><code>/public *(ro,sync,no_subtree_check)
/private [CLIENT IP ADDRESS](rw,sync,no_subtree_check)</code></p>

<pre><code>sudo exportfs -arvf</code></pre>
<pre><code>sudo systemctl start nfs-kernel-server</code></pre>
<pre><code>sudo systemctl status nfs-kernel-server</code></pre>

<h1>Configure NFS Client</h1>
<pre><code>sudo apt-get install nfs-common</code></pre>
<pre><code>showmount -e [SERVER IP-ADDRESS]</code></pre>
<pre><code>sudo mkdir /mnt/public</code></pre>
<pre><code>sudo mkdir /mnt/private</code></pre>
<pre><code>sudo mount -t nfs [SERVER IP-ADDRESS]:/public /mnt/public</code></pre>
<pre><code>sudo mount -t nfs [SERVER IP-ADDRESS]:/private /mnt/private</code></pre>
<pre><code>mount</code></pre>



</body>
