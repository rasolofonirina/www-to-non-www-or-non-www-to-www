# Redirect www to non-www or non-www to www

EN : If for some reason you need to redirect the www version of your website to the non-www version or the non-www version to the www version, you can use these instructions on the `.htaccess` file.

FR : Si pour une raison ou une autre vous avez besoin de rediriger la version www de votre site web vers la version sans www ou la version sans www vers la version www, vous pouvez utiliser ces instructions sur le fichier `.htaccess`.

## With HTTP (avec HTTP)

```
# Redirect non-www to www
RewriteEngine On
RewriteCond %{HTTP_HOST} ^example\.com [NC]
RewriteRule ^(.*)$ http://www.example.com/$1 [L,R=301]
```

```
# Redirect www to non-www
RewriteEngine On
RewriteCond %{HTTP_HOST} ^www.example\.com [NC]
RewriteRule ^(.*)$ http://example.com/$1 [L,R=301]
```

## With HTTPS (avec HTTPS)

EN : If the SSL certificate is installed and activated on the hosting and you want to have HTTPS.

FR : Si le certificat SSL est installé et activé sur l'hébergement et que vous souhaitez avoir HTTPS.

```
# Redirect non-www to www with HTTPS
RewriteEngine On
RewriteCond %{HTTPS} !=on
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteCond %{HTTP_HOST} ^example\.com [NC]
RewriteRule ^(.*)$ https://www.example.com/$1 [L,R=301]
```

```
# Redirect www to non-www with HTTPS
RewriteEngine On
RewriteCond %{HTTPS} !=on
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteCond %{HTTP_HOST} ^www.example\.com [NC]
RewriteRule ^(.*)$ https://example.com/$1 [L,R=301]
```