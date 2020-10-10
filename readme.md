

If you are using Apache with CGI/FastCGI, then you might get an error message about missing authorization headers. This is because Apache does not, by default, pass authorization headers to PHP.

The Fix

You need to edit your Apache site configuration to add a line to Deskpro's <VirtualHost> directive. Note that this configuration must be added directly to Apache's configuration (e.g., adding it to htaccess will not work).

 

<VirtualHost>
    # ...
    SetEnvIf Authorization "(.*)" HTTP_AUTHORIZATION=$1
    # ...
</VirtualHost>