Private Chef Ports
~~~~~~~~~~~~~~~~~~~

The ports are all tcp protocol unless otherwise noted.

====================   =======
 Service                Port 
~~~~~~~~~~~~~~~~~~~~

 Backends
====================   =======
 drbd                   7788
 keepalived (raw)       112
 solr                   8983
 rabbitmq               5672
 couchdb                5984
 postgresql             5432
 redis                  6379
 bookshelf              4321
 opscode-chef           9460
 opscode-erchef         8000
 opscode-authz          9463
 opscode-certificate    5140
 opscode-org-creator    4369
 opscode-account        9465
 opscode-reporting      10010
 estatsd (udp)          9466
 nagios                 9671
 nrpe                   9672
====================   =======



====================   =======
 Frontends              Port 
====================   =======
 opscode-webui          9462
 nginx ssl              443
 nginx non-ssl          80 
====================   =======
