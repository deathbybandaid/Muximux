# phpinfo meets muximux,,, just something I tossed together on the work of others.

# All real praise goes to Tenzinn3 and Mescon




# Muximux - Lightweight HTPC portal

## Setup

**Requirements:** A webserver (nginx, Apache, IIS or any other webserver) configured with PHP5 support.
`` parse_ini_file `` must be allowed in php.ini (default is allowed!)

- Place all files on a publically accessible webserver, either in a subdirectory called ``phpinfo`` or directly in the root directory of your webserver (such as ``/var/www``, ``/var/html``, ``C:\Inetpub\wwwroot`` or wherever your webserver serves files from by default).

- [Read this note](#security) about securing Muximux, and [read this note](#important-note-regarding-https) about what happens if you are using HTTPS. Just do it.

- Make sure that the directory where you place Muximux is [writable by the process that is running your webserver](http://lmgtfy.com/?q=how+to+make+a+directory+writable+by+my+webserver). *(i.e www-data, www-user, apache, nginx or whatever the user is called)*
  - Example: ``chown -R www-data.www-data /var/www/phpinfo``

### Security
**It is strongly recommended that you secure Muximux with Basic Auth (``.htpasswd / .htaccess``)**

Read instructions for [Nginx](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04), [Apache](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-apache-on-ubuntu-14-04) and [Microsoft IIS](http://serverfault.com/a/272292).

If you decide not to, Muximux disallows search engines from indexing your site, however, Muximux itself does not password protect your services, so you have to secure each of your applications properly (which they already should be!).
Muximux is NOT a proxy server, and as such can not by itself secure your separate applications, and if you don't want Muximux to be open to the world, you *must* make sure that you have Basic Auth enabled on your server.

### Important note regarding HTTPS
 If you are serving Muximux from a HTTPS-enabled webserver (i.e``https://myserver.com/muximux``), all of your services must also be secured via HTTPS.
 Any URL that does not start with https:// (such as ``http://myserver.com:5050``) will be blocked by your web-browser!

 If you can, try serving Muximux from a non-secure (HTTP) webserver instead.
 If the apps you have configured are using HTTPS, communication with them will still be encrypted.

 The only known workaround is for Chrome, Opera and Chromium-based webbrowsers.

 Install the plugin "[Ignore X-Frame headers](https://chrome.google.com/webstore/detail/ignore-x-frame-headers/gleekbfjekiniecknbkamfmkohkpodhe)" which disables the blocking of non-secure content.
