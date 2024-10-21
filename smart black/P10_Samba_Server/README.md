<h1>Aim: Install Samba to share folders or files between Windows and Linux.</h1>
<h2>Server Side</h2>
<pre><code>sudo apt get install samba</code></pre>
<pre><code>sudo mkdir /share</code></pre>
<pre><code>sudo chmod 777 /share</code></pre>
<pre><code>sudo nano /etc/samba/smb.conf</code></pre>
<p><code>[my-samba-share]
  path = /share
  public = no
  valid users = tom, jerry
  read list = tom
  write list = jerry
  browseable = yes
  comment = "My samba file server"
</code></p>
<pre><code>sudo testparm</code></pre>
<pre><code>sudo useradd tom -s /sbin/nologin</code></pre>
<pre><code>sudo useradd jerry -s /sbin/nologin</code></pre>
<pre><code>sudo smbpasswd -a tom</code></pre>
<pre><code>sudo smbpasswd -a jerry</code></pre>
<pre><code>sudo systemctl start smbd</code></pre>
<pre><code>sudo systemctl start nmbd</code></pre>
<pre><code>sudo systemctl enable smbd nmbd</code></pre>


<h2>Client Side </h2>
<pre><code>ping [SERVER IP-ADDRESS]</code></pre>
<p><code>Then open File Manager -> Other Locations -> connect to server -> smb://[SERVER IP-ADDRESS]</code></p>
<p><code>From radio button click on register user and login with valid username password</code></p>
<h2>Windows Client Side </h2>
<p><code>Press window + R then enter cmd. And then ping the server to check whether we are in the network or not.</code></p>
<pre><code>\\[SERVER IP-ADDRESS]</code></pre>
<p><code>Login with valid username password</code></p>

