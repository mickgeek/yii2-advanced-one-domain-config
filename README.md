Yii 2 Advanced Application. One Domain Configuration
===

There are times when there is no need or no possibility to place the frontend and backend parts on different domains. Here are the instructions for configuration of the Apache or Nginx web servers for using multiple applications on a single domain.

**Final frontend URL: http://advanced.local**  
**Final backend URL: http://advanced.local/admin**

Preparation
---

You need to make some changes in the configuration files of the applications according to the bundled `advanced/frontend/config/main.php` and `advanced/backend/config/main.php` files.

The next step is the adding two rules from the bundled `advanced/frontend/web/robots.txt` file to the content of your main `robots.txt` file.

Apache Configuration (.htaccess or VirtualHost)
---

> Note: If you have **a shared hosting** or want to use `.htaccess`, simply copy the bundled `advanced/.htaccess` file into the root directory of your project.

The first thing to do is to execute the following command with enough permissions to make sure whether the `mod_rewrite` module is enabled:

```bash
[ -f /etc/apache2/mods-enabled/rewrite.load ] && echo "Found" || echo "Not Found"
```

If the `Not Found` message appears, just execute the `a2enmod rewrite` command and restart the Apache server.

Now you can use the configuration specified in the bundled `vhosts/apache.conf` file to set up a virtual host. But don't forget to replace `advanced.local` with an actual hostname and `/path/to/advanced` with an actual path.

Nginx Configuration
---

In this case, use only the configuration of the bundled `vhosts/nginx.conf` file. If you don't like use `advanced.local` as a hostname, change it. Also replace `/path/to/advanced` with the actual path to your project.

---

Inspired by discussions in [the russian community] of the Yii framework.

[the russian community]:https://yiiframework.ru/
