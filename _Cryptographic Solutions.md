
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
 - Login: admin
 - Pass: pass
  
 - Login: sec#$34T#
 - Pass: pass 

 - Login: yourNickname
 - Pass: pass

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

## Exercise 01 - Modify permissions 

| Account   | Permissions |
| ---       | ---         |
| admin     | drwx-wxr-x  |
| rivan     | drwxrw-rw-  |
| sec#$34T# | drw-rw-rw-  |

<br>






Add groups
@NetOps
groupadd HR
groupadd SEC
groupadd CA


Exercise 02 - Modify user accounts to achieve the following
  - admin is part of HR, SEC, CA, and is a sudoer
  - rivan is part of SEC and HR
  - sec#$34T# is part of SEC and CA


@NetOps
usermod -aG HR,SEC,CA admin


File Sharing
@NetOps
chown admin:HR admin
chown rivan:SEC rivan
chown sec#$34T#:CA sec#$34T


TIP: Don't forget about file permissions


Recursive permissions
@NetOps
chmod +s SEC



__________
**********
Public Key Authentication (Linux)

@NetOps
cd /tmp
mkdir keys
cd keys

Create a Private key.

@NetOps
openssl genrsa -aes256 -out admin.pem 2048

Extract public key from private key
@NetOps
openssl rsa -in admin.pem -pubout -out admin_pub.pem
