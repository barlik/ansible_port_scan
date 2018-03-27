Port scan role
--------------

This role is used to check for network connectivity between nodes
according to rules saved in `firewall_rules` variable. The role
generates a csv file with the connectivity details.

Sample playbook
---------------

        ---
        - hosts: all
          tasks:
            - yum: name=nmap-ncat
              become: true

        - hosts: localhost
          connection: local
          roles:
            - { role: port_scan, report_file: /tmp/report/report.txt }

Sample inventory
----------------

        [internal_elb_master:children]
        master

        [elb_master:children]
        master

        [master]
        10.0.0.1

        [etcd]
        10.0.0.2

        [node]
        10.0.0.3

        [infra_node]
        10.0.0.4

        [router]
        10.0.0.5
