collectd-collector
==================

OpenShift nodejs cartridge to collect data from Collectd write_http plugin

Collectd Setup
==================
The write_http plugin needs to be configured to report to the node server.
Make the following change in collectd.conf and replace `LISTENER_HOSTNAME` with your server's FQDN.

```
LoadPlugin write_http
<Plugin "write_http">
  <URL "http://LISTENER_HOSTNAME/json">
    Format "JSON"
  </URL>
</Plugin>
```

Viewing Collectd Reports
================
collectd-collector writes the incoming collectd reports to `/json/data.json`. Using a browser you can view the latest report at `http://LISTENER_HOSTNAME/data`.

Common Errors
=================
* `http://LISTENER_HOSTNAME/data` Only responds with `{}`
 * Check that your server is recieving POST commands at `/json`. Use a tool like the Chrome plugin Postman.
 * Check that the `write_http` plugin was compiled in your deployment of Collectd. The `write_http` plugin depends on curl and curl-config during compilation. So you may need to install those applications before recompiling collectd. You can see which plugins have been compiled by looking in the `collecd.conf` file. Any plugins preceeded by `##` were not compiled.
