# Domain Controllers
A domain controller is a Windows server that has Active Directory Domain Services (AD DS) installed and has been promoted to a domain controller in the forest. Domain controllers are the centre of an Active Directory network, they control the rest of the domain.

The main tasks of a Domain Controller is:
- holds the AD DS data store
- handles authentication and authorization services
- replicate updates from other domain controllers in the forest
- allows admin access to manage domain resources

# AD DS
The Active Directory Data Store hols the databases and processes needed to store and manage directory information, such as users, groups and services.

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




