[README]

Edit the variable file setup.yml with the desired settings

$ cat setup.yml 
gluster:
  brick: /var/bricks/brick
  volume_name: gluster_test_vol
  volume_mount_point: /vol/gluster_mount

Either ensure that the hostnames of all gluster peers can be resolved via DNS or edit templates/hosts.j2 

$ cat templates/hosts.j2 
127.0.0.1   {{ ansible_hostname }} {{ ansible_hostname }}.{{ansible_domain}}
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
192.168.33.11 gluster1 gluster1.dev
192.168.33.12 gluster2 gluster2.dev

Edit the hosts file and add servers to the gluster group, best to use a FQDN

$ cat hosts 
[gluster]
gluster1.dev
gluster2.dev


