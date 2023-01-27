---
password: 'secret'
---
# Guide to the Local Workstations and Clusters

## Access Office Workstations
___
You can connect to the workstations with your personal computer. You will need to use a secure shell connection (ssh). Then, you need to be inside the UCL firewall, which usually happens when you are in the office (though, this may still not work, in that case, use the [External Access](#external-access---ucl-gateway)

#### Linux / Unix / MacOs
Use the terminal and type the below command to secure shell (ssh) into the machine you wish to access. Replace <your_user_name> with your assigned user name for the workstations, and <workstation_name> with the name of the machine you want to log in to, eg. [Turing](#turing), [Curie](#curie), [Fourier](#fourier).

``` ssh <your_user_name>@<system_name>.phys.ucl.ac.uk ```

#### Windows
On Windows you need something that will give you a suitable terminal and ssh - usually PuTTY, or on Windows 10 you can use OpenSSH from a command prompt and type the same ssh command as the [Linux instructions](#linux--unix--macos).

### External Access - UCL Gateway
You will need to either use the [UCL Virtual Private Network](https://www.ucl.ac.uk/isd/services/get-connected/ucl-virtual-private-network-vpn/) or ssh in to UCL's Gateway system ```ssh-gateway.ucl.ac.uk``` first. In this case, you have to use your UCL User Id (i.e. ucXXXX). 
``` ssh <your_UCL_user_id>@ssh-gateway.ucl.ac.uk ```
From there you can then ssh in to the workstations as explained above.

## Access UCL clusters
___
### Myriad / Kathleen / Thomas
## Access National Clusters
___
### ARCHER
### MMM Young
### JADE2
## Workstations
___
#### Turing
- IP address: turing.phys.ucl.ac.uk
- Hardware - Less Beefy
- Storage Available
- Admins
#### Coulomb
- IP address: coulomb.phys.ucl.ac.uk
- Hardware - Beefiest
- Storage Available
- Admins
#### Fourier
- IP address: fourier.phys.ucl.ac.uk
- Hardware - Alright
- Storage Available
- Admins
#### Curie
- IP address: curie.phys.ucl.ac.uk
- Hardware - ???
- Storage Available
- Admins

