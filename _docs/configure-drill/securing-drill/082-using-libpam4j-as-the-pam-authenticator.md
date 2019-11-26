---
title: "Using libpam4j as the PAM Authenticator"
date: 2017-12-18 01:38:50 UTC
parent: "Securing Drill"
---


The libpam4j module is packaged with Drill. The libpam4j module does not have any external dependencies.  

To use libpam4j as the PAM authenticator with Drill, complete the following steps:

1.drill是集群运行模式。

2.运行`<DRILL_HOME>/bin/drill-localhost`，进入交互界面，设置管理员账号：
```
Apache Drill 1.16.0
"A Drill in the hand is better than two in the bush."
apache drill> alter system set security.admin.users = 'youlinuxuser';
+------+-------------------------------+
|  ok  |            summary            |
+------+-------------------------------+
| true | security.admin.users updated. |
+------+-------------------------------+
1 row selected (1.397 seconds)
```
3. Add the following configuration to the `drill.exec` block in the `<DRILL_HOME>/conf/drill-override.conf` file:  
  
              drill.exec: {
               cluster-id: "drillbits1",
               zk.connect: "<zk-node-hostname>:2181,<zk-node-hostname>:2181,<zk-node-hostname>:2181",
               impersonation: {
                 enabled: true,
                 max_chained_user_hops: 3
               },
               security: {          
                       auth.mechanisms : ["PLAIN"],
                        },
               security.user.auth: {
                       enabled: true,
                       packages += "org.apache.drill.exec.rpc.user.security",
                       impl: "pam4j",
                       pam_profiles: [ "sudo", "login" ]
                }
              }

4. (Optional) To add or remove different PAM profiles, add or delete the profile names in the `pam_profiles` array in the configuration.
5. Restart the Drillbit process on each Drill node, as shown:  

              <DRILLINSTALL_HOME>/bin/drillbit.sh restart


