collectd-collector
==================

OpenShift nodejs cartridge to collect data from Collectd write_http plugin

Collectd Setup
==================
The write_http plugin needs to be configured to report to the node server.
Make the following change in collectd.conf

'''
<Plugin "write_http">
  <URL "http://LISTENER_HOSTNAME/json">
    Format "JSON"
  </URL>
</Plugin>
```
