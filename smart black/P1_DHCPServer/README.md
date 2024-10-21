<body>

<h1>Server Side Configuration</h1>

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
<p>- <code>auto lo</code></p>
<p>- <code>iface lo inet loopback</code></p>
<p>- <code>auto ens33</code></p>
<p>- <code>iface ens33 inet dhcp</code></p>

<pre><code>ip a</code></pre>
<pre><code>sudo systemctl restart networking</code></pre>

<h1>Server Side to Check Connection</h1>
<pre><code>sudo nano /var/lib/dhcp/dhcpd.leases</code></pre>

</body>
