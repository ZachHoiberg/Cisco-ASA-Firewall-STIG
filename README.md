# Cisco-ASA-Firewall-STIG

1. Create an ansible vault at ./secrets/secrets.yaml

2. This Vault should contain the following formatted as such:
recipientAddress: email@domain.com
emailDomain: emaildomain.com
smtpServer: smtpServer
logHost: logHost
loggingInterface: outside
tunnelGroups: |-
        10.1.1.1
groupPolicyName: GroupPolicy1
vpnFilterACLName: RESTRICT_VPN
vpnFilterACL: |-
        access-list RESTRICT_VPN extended permit ip object X object Y
        access-list RESTRICT_VPN extended deny ip any any log default
insideInACL: |-
        access-list inside_access_in extended permit ip object X object Y
        access-list inside_access_in extended deny ip any any log default
insideOutACL: |-
        access-list inside_access_out extended deny udp any any eq snmp
        access-list inside_access_out extended deny udp any any eq snmptrap
        access-list inside_access_out extended deny udp any any eq ntp
        access-list inside_access_out extended deny udp any any eq syslog
        access-list inside_access_out extended deny tcp any any eq ssh
        access-list inside_access_out extended deny tcp any any eq tacacs
        access-list inside_access_out extended permit ip any any
        access-list inside_access_out extended deny ip any any log default
outsideInACL: |-
        access-list outside_access_in extended permit ip object X Y LOCALSUBNET
        access-list outside_access_in extended deny ip any any log default
outsideCryptomapACL: |-
        access-list outside_cryptomap extended permit ip object X object Y
        access-list outside_cryptomap extended deny ip any any log default
        
3. Create inventory file

4. Run playbook
