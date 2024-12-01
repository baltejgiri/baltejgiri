# VLAN Trunking Lab using Aruba Switches

### Introduction

I have used [HPE Aruba Networking CX Switch](https://www.hpe.com/us/en/aruba-cx-switches.html) in this lab to configure VLAN Trunking. HPE Aruba Networking CX switches are hosted on emulator ["EVE-NG"](https://www.eve-ng.net/).

![HPE Aruba VLAN Trunking Design](/images/hpe_aruba_switches_stack.png)

This is a VLAN trunking lab, I am using two VLANs, VLAN 10 and 20. The command line interface of Aruba cx switches is similar to Cisco catalyst series switches which makes it easier to navigate through. 

### Design
I am choosing a simple design selecting two switches and four VPC endpoints. Therefore, I assigned two VPC’s to VLAN 10 and two to VLAN 20 across both switches yet separating them between both switches. I picked two network address 10.1.10.0 and 10.1.20.0 with /24 subnet mask. Each VPC is assigned with an IP address respective to its VLAN number (demonstrated in network diagram).

![HPE Aruba VLAN Trunking Design](/images/hpe_aruba_vlan_trunking_design.png)

### Configuration

This part took some digging, but with the help of question mark (?) in CLI of switch and "show commands" helped me to configure these switches with access links and trunk links. The configuration steps I took was to create VLANs and naming them as per design. The interfaces connected to endpoints are in access mode allowing native VLANs and VLAN as per design. The inter-switch between both switches are in trunking mode only allowing traffic for VLANs 10 and 20. The trunk link is limited to VLANs 10 and 20 as a best practice so unnecessary traffic or broadcast storm does not affect the whole network.

I have attached a reference link from Aruba which gives a great overview of commands used in Aruba switches.

### Verification

I used ping command to check connectivity from one VPC to another within the same VLAN yet they are on different switches which proves the concept of VLAN tagging. I also used Wireshark to analyze the Ethernet frames. The attached two screenshots depicts how a 802.1Q frame look like and the ID number it carries for a VLAN.

### Summary

At last, it was a good learning exercise where i have familiarized myself with HPE Aruba Switches. The overall experience was excited and I like that Aruba switches has similar command line interfaces to Cisco’s Catalyst but with some improvements i.e. being able to run show commands at any mode without needing a ‘do’ syntax.

### References
   [Draw.io](https://lnkd.in/gWmSgJnc)

   [EVE-NG](https://www.eve-ng.net/)
   
   [HPE Aruba](https://www.hpe.com/ca/en/home.html)
