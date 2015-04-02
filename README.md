Yii 2 Advanced Application. One Domain Configuration
===

There are times when there is no need or no possibility to place the frontend and backend parts on different domains. Here are the instructions for configuration of the Apache or Nginx web servers for use multiple applications on the same domain.

**Final frontend URL: http://advanced.local**  
**Final backend URL: http://advanced.local/admin**

Preparation
---

You need to make some changes to the configuration files of the applications according to the bundled `advanced/frontend/config/main.php` and `advanced/backend/config/main.php` files.

Apache Configuration
---

The first thing to do is to execute the following command with enough permissions to make sure whether the `mod_rewrite` module is enabled:

```bash
[ -f /etc/apache2/mods-enabled/rewrite* ] && echo "Found" || echo "Not Found"
```

If the `Not Found` message appears, just execute the `a2enmod rewrite` command and restart the Apache server.

Now you can to use the configuration specified in the bundled `vhosts/apache.conf` file for setting up a virtual host. But don't forget to replace `advanced.local` with the actual hostname and `/path/to/advanced` with the actual path.

> Note: If you have a shared hosting, simply copy the bundled `advanced/.htaccess` file to the root directory of your project.

The final step is to add to the contents of the main `robots.txt` file two rules from the bundled `advanced/frontend/web/robots.txt` file.

Nginx Configuration
---

In this case, use only the configuration of the bundled `vhosts/nginx.conf` file. If you don't like `advanced.local` as a hostname, change it. Replace also `/path/to/advanced` with the actual path to your project.
