Picture yourself administering a small business network with only five computers and five employees. In such a tiny network, you will probably be able to configure each computer separately without a problem. You will manually log into each computer, create users for whoever will use them, and make specific configurations for each employee's accounts. If a user's computer stops working, you will probably go to their place and fix the computer on-site.

While this sounds like a very relaxed lifestyle, let's suppose your business suddenly grows and now has 157 computers and 320 different users located across four different offices. Would you still be able to manage each computer as a separate entity, manually configure policies for each of the users across the network and provide on-site support for everyone? The answer is most likely no.

To overcome these limitations, we can use a Windows domain. Simply put, a Windows domain is a group of users and computers under the administration of a given business. The main idea behind a domain is to centralise the administration of common components of a Windows computer network in a single repository called Active Directory (AD). The server that runs the Active Directory services is known as a Domain Controller (DC).

Windows Domain Overview

# Domain Controllers
A domain controller is a Windows server that has Active Directory Domain Services (AD DS) installed and has been promoted to a domain controller in the forest. Domain controllers are the centre of an Active Directory network, they control the rest of the domain.

The main tasks of a Domain Controller is:
- holds the AD DS data store
- handles authentication and authorization services
- replicate updates from other domain controllers in the forest
- allows admin access to manage domain resources

# AD DS
TThe core of any Windows Domain is the Active Directory Domain Service (AD DS). This service acts as a catalogue that holds the information of all of the "objects" that exist on your network. Amongst the many objects supported by AD, we have users, groups, machines, printers, shares and many others.

Here is an outline of the contents and characteristics of the AD DS:

- contains the NTDS.dit – a database that contains all the information of an Active Directory domain controller as well as password hashes for domain users
- stored by default in %SystemRoot%\NTDS
- accessible only by the domain controller

# Users
There are 4 main types of users you’ll find in an Active Directory network, however that depends on how a company manages the permissions of its users.

The four types of users are:

- Domain Admins – The big boss, they control the domains and the only one with access to the domain controller
- Service Accounts (can be Domain Admins) – These are mainly for network services such as SQL to pair a service with a service account.
- Local Administrators – These users can make changes to local machines as an administrator and may even be able to control other normal users, but they can’t access the domain controller.
- Domain Users – These are the everyday users. They can log in on the machines they are authorized to access and may have local admin rights to certain machines (depending on the organization).

# Groups
Groups make it easier to give permissions to users and objects by organizing them into groups with specific permissions. There are two overarching types of Active Directory groups:

- Security Groups – These groups are used to specify permissions for a large number of users.
- Distribution Groups – These groups are used to specifcy email distribution lists. As an attacker these groups can be beneficial in enumeration.

# Domain Trusts
Trusts are a mechanism in place for users in the network to gain access to other resources in the domain. This means basically that the trusts outline the way that the domains interact inside of a forest communicate with each other. In some environments trusts can be extended out to external domains and even forests in some cases.

# Domain Policies
Policies are a very big part of Active Directory – they dictate how the server operates and what rules it needs to follow. You can think of domain policies like domain groups, except instead of permissions they contain rules, and instead of only applying to a group of users, the policies apply to a domain as a whole. Domain policies act as a rulebook for Active Directory that a domain admin can modify and alter as they deem necessary to keep the network running smoothly and securely.




