
<!-- Your monitor number = #$34T# -->

# Linux user account management

Access __NetOps__ VM
 - Login: `root`
 - Pass: `C1sc0123`

<br>

Get the IP of your VM and establish an SSH session in SecureCRT.

```
@NetOps
ip -4 addr
```

### Task 01 - Create the following user accounts:
| Login     | Pass |
| ---       | ---  |
| admin     | pass |
|           |      |
| sec#$34T# | pass |
|           |      |
| _________ | pass |


```
@NetOps
useradd admin
passwd admin

New Password: pass
Retype New Password: pass
```
>[!Note]
>Ignore the BAD PASSWORD

---

### Task 02 - Create accounts with the `nologin` option.
```
@NetOps
useradd -s /sbin/nologin secblock
```

Why nologin? For backend services
```
@NetOps
grep nologin /etc/passwd
```

---

### Task 03 - Managing file permissions

```
@NetOps
cd /etc
ls -lh
```

| Type of file| Owner | Group | Others |
| ---         | ---   | ---   | ---    |
|     d       |  rwx  | r-x   | r-x    |

<br>

Scoring Value
__Read__ `4` - __Write__ `2` - __Execute__ `1`

```
@NetOps
chmod 777 filename
```

Common Permissions
 - 644 - File Baseline
 - 755 - Directory Baseline
 - 400 - Key pair

```
@NetOps
cd /home
ls -la
```

---

## Exercise 01 - Modify permissions 

| Account   | Permissions |
| ---       | ---         |
| admin     | drwx-wxr-x  |
| rivan     | drwxrw-rw-  |
| sec#$34T# | drw-rw-rw-  |

<br>




---

### Add groups
```
@NetOps
groupadd HR
groupadd SEC
groupadd CA
```

---

### Exercise 02 - Modify user accounts to achieve the following:
  - admin is part of HR, SEC, CA, and is a sudoer
  - rivan is part of SEC and HR
  - sec#$34T# is part of SEC and CA

```
@NetOps
usermod -aG HR,SEC,CA admin
```

---

### File Sharing
```
@NetOps
chown admin:HR admin
chown rivan:SEC rivan
chown sec#$34T#:CA sec#$34T
```

>[!TIP]
>Don't forget about file permissions

Recursive permissions
```
@NetOps
chmod +s SEC
```

---

# Privilege Access Management
Open NetOps VM IP on a browser
 - User: admin
 - Pass: C1sc0123

For an SSH connection to be established, the device must have:
    - a non-default hostname         hostname coreBaba#$34T#
    - a domain name                  ip domain name day1lab.com
    - a local user account           username admin privilege 15 secret pass
    - generated crypto keys          crypto key generate rsa modulus 2048
    - SSH enabled                    ip ssh version 2
    - enable remote access           transport input all
    - enable remote user/pass login  login local

Extra lines
    - password encryption            service password-encryption
    - no logs                        no logging console
    - no domain lookups              no ip domain-lookup
    - no timeout                     exec-timeout 0 0

```
@coreTaas
conf t
 hostname coreTaas-#$34T#
 service password-encryption
 no logging console
 no ip domain-lookup
 ip domain name autoday1.com
 username rivan privilege 15 secret pass
 username admin privilege 15 secret pass
 line vty 0 14
  transport input all
  login local
  exec-timeout 0 0
  exit
 crypto key generate rsa modulus 2048 label devs
 ip ssh rsa keypair-name devs
 ip ssh version 2
 end
```
```
@coreBaba
conf t
 hostname coreBaba-#$34T#
 service password-encryption
 no logging console
 no ip domain-lookup
 ip domain name autoday1.com
 username rivan privilege 15 secret pass
 username admin privilege 15 secret pass
 line vty 0 14
  transport input all
  login local
  exec-timeout 0 0
  exit
 crypto key generate rsa modulus 2048 label devs
 ip ssh rsa keypair-name devs
 ip ssh version 2
 end
``` 
```
@cucm
conf t
 hostname cucm-#$34T#
 service password-encryption
 no logging console
 no ip domain-lookup
 ip domain name autoday1.com
 username rivan privilege 15 secret pass
 username admin privilege 15 secret pass
 line vty 0 14
  transport input all
  login local
  exec-timeout 0 0
 crypto key generate rsa modulus 2048 label devs
 ip ssh rsa keypair-name devs
 ip ssh version 2
 end
```
```
@edge
conf t
 hostname edge-#$34T#
 service password-encryption
 no logging console
 no ip domain-lookup
 ip domain name autoday1.com
 username rivan privilege 15 secret pass
 username admin privilege 15 secret pass
 line vty 0 14
  transport input all
  login local
  exec-timeout 0 0
 crypto key generate rsa modulus 2048 label devs
 ip ssh rsa keypair-name devs
 ip ssh version 2
 end
```

```
@UTM-PH
conf t
 hostname UTM-#$34T#
 service password-encryption
 no logging console
 no ip domain-lookup
 ip domain name autoday1.com
 username rivan privilege 15 secret pass
 username admin privilege 15 secret pass
 line vty 0 14
  transport input all
  login local
  exec-timeout 0 0
 crypto key generate rsa modulus 2048 label devs
 ip ssh rsa keypair-name devs
 ip ssh version 2
 end
```

```
@NetOps
cd /tmp
mkdir keystore
cd keystore
```

### Create a Private key.
```
@NetOps
ssh-keygen -t rsa -b 2048 -f admin
```

---

### Apply keys to user accounts
```
@UTM-PH
conf t
 ip ssh pubkey-chain
  username rivan
   key-string
```

```
@NetOps
cd /root/.ssh/
cat identity.pub >> authorized_keys
```


### Turn off password authentication for Cisco and Linux.
@NetOps
cd /etc/ssh/sshd_config
