<h1>
  Aim: Install MySQL to configure database server, Install phpMyAdmin to operate MySQL on web browser from Clients.
</h1>
<pre><code>sudo apt install apache2</code></pre>
<h3>Open browser and type localhost</h3>

<p>Create a file in /var/www/html such as test.html and run on browser localhost/test.html</p>
<pre><code>sudo apt-get install libapache2-mod-php</code></pre>
<pre><code>sudo apt-get install mysql-server mysql-client</code></pre>
<p><code>Ask to create password</code></p>
<pre><code>mysql -u root -p</code></pre>
<pre><code>sudo apt-get install phpmyadmin</code></pre>
<p><code><b>Ask some questions</b></code></p>
<p><code>Web server to configure automatically <b> apache2</b></code></p>
<p><code>Configure database for phpmyadmin with dbconfig-common? <b>No</b></code></p>
<pre><code>sudo service apache2 restart</code></pre>
<p><code>Browse to localhsot/phpmyadmin on your web browser</code></p>
<p><code>Create database using GUI</code></p>
