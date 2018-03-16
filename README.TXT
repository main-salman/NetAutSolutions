Hi Ivan,

I have a simple setup. I have VIRL running with four interconnected devices. They have a port
connected to the FLAT network, which I am using as the "management" network.

I have another Ubuntu VM running with Ansible/NAPALM.

Here is output from that Ubuntu VM contacting the routers to collect ARP entries.

Thanks,

Salman Naqvi
+1-647-632-1600

user@ubuntu:~/ansible$ ansible-playbook -i ansible_hosts tasks.yml 
PLAY [all] **********************************************************************************************

TASK [Display the device's ARP table] *******************************************************************
changed: [dc1-core1]
changed: [dc2-core1]

TASK [debug] ********************************************************************************************
ok: [dc1-core1] => {
    "show.stdout_lines": [
        "", 
        "Flags: * - Adjacencies learnt on non-active FHRP router", 
        "       + - Adjacencies synced via CFSoE", 
        "       # - Adjacencies Throttled for Glean", 
        "       D - Static Adjacencies attached to down interface", 
        "", 
        "IP ARP Table for context default", 
        "Total number of entries: 1", 
        "Address         Age       MAC Address     Interface", 
        "192.168.0.130   00:07:53  a088.b4c0.56c8  Ethernet2/3     "
    ]
}
ok: [dc2-core1] => {
    "show.stdout_lines": [
        "", 
        "Flags: * - Adjacencies learnt on non-active FHRP router", 
        "       + - Adjacencies synced via CFSoE", 
        "       # - Adjacencies Throttled for Glean", 
        "       D - Static Adjacencies attached to down interface", 
        "", 
        "IP ARP Table for context default", 
        "Total number of entries: 1", 
        "Address         Age       MAC Address     Interface", 
        "192.168.0.130   00:07:53  a088.b4c0.56c8  Ethernet2/3     "
    ]
}

PLAY RECAP **********************************************************************************************
dc1-core1                  : ok=2    changed=1    unreachable=0    failed=0   
dc2-core1                  : ok=2    changed=1    unreachable=0    failed=0  


