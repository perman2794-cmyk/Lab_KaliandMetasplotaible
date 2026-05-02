# 🛡️ Laboratorio de Explotación: Kali Linux vs. Metasploitable2

Este laboratorio documenta la interacción técnica entre una máquina atacante (Kali Linux) y una víctima controlada (Metasploitable2), detallando el proceso desde la configuración de red hasta la explotación exitosa.

---

## 👥 Integrantes del Equipo
*   **Maria Alejandra Nuñez**
*   **Efrain Yaird Diaz Anzola**
*   **Fabian Andres Perilla Manjarres**

---

## ⚙️ Configuración del Entorno Virtual

### 🌐 Configuración de Red (Modo Host-Only)
Para garantizar un entorno seguro y aislado, ambas máquinas se configuraron en modo **Host-Only**.

**Metasploitable2:**
<img width="990" height="924" alt="Configuración Red Metasploitable" src="https://github.com/user-attachments/assets/e6aa30f6-79eb-4c4c-ad4b-a09f44cf5fe8" />

**Kali Linux:**
<img width="1017" height="909" alt="Configuración Red Kali" src="https://github.com/user-attachments/assets/df8ac078-3ac8-4f06-9983-68ce64cacdd6" />

---

### 🐧 Instalación de Kali Linux
Proceso de despliegue de la plataforma de seguridad.

<img width="921" height="476" src="https://github.com/user-attachments/assets/4a5ae3ac-306b-4753-843d-9dfe271bb847" />
<img width="921" height="481" src="https://github.com/user-attachments/assets/0dbef766-eb59-4d98-8732-a397f35f58b9" />
<img width="921" height="479" src="https://github.com/user-attachments/assets/1ea5536c-8691-44ef-83f1-aeefdf9a1c5a" />

---

## 🕵️ Reconocimiento y Conectividad

### 📍 Identificación de Direcciones IP
*   **IP Kali Linux:** 192.168.164.128  
    <img width="1142" height="469" src="https://github.com/user-attachments/assets/3143805c-6433-4ee1-a209-d756172bc418" />
*   **IP Metasploitable2:** 192.168.164.129  
    <img width="1071" height="502" src="https://github.com/user-attachments/assets/b7b46aaa-69cb-428f-a7b7-82194fd35e6a" />

### 📡 Pruebas de Comunicación (ICMP)
**Ping de Metasploitable2 a Kali:**
<img width="861" height="293" src="https://github.com/user-attachments/assets/97a7df42-7bda-49d5-8b04-5bf08eee26fd" />

**Ping de Kali a Metasploitable2:**
<img width="961" height="354" src="https://github.com/user-attachments/assets/4bba98cc-1f95-4dba-b131-00684aa12c8f" />

---

## 🔍 Auditoría de Red y Escaneo de Vulnerabilidades

### 🛠️ Descubrimiento con Netdiscover
Identificación de dispositivos activos en la red local.
<img width="773" height="203" src="https://github.com/user-attachments/assets/aa46a22d-bb52-4ee3-9796-615625fbb20c" />

### 📊 Reporte de Escaneo Nmap
Realización de la explotación a la IP **192.168.164.129**.

<img width="744" height="180" alt="image" src="https://github.com/user-attachments/assets/74099f2d-99eb-4e36-82f9-20edd5a4a2a3" />

### Output de la aplicacion del comando:

zsh: suspended  sudo netdiscover -r 192.168.68.0
                                                                                                                                                                                                                   
┌──(fea㉿fea)-[~]
└─$ nmap -sV -sC -p -T4 -oN nmap_scan_metasploitable2.txt 192.168.164.1_
Starting Nmap 7.98 ( https://nmap.org ) at 2026-05-01 21:57 -0400
Error #486: Your port specifications are illegal.  Example of proper form: "-100,200-1024,T:3000-4000,U:60000-"
QUITTING!
                                           
┌──(fea㉿fea)-[~]
└─$ nmap -sV -sC  -T4 -oN nmap_scan_metasploitable2.txt 192.168.164.1_ 
Starting Nmap 7.98 ( https://nmap.org ) at 2026-05-01 21:58 -0400
Failed to resolve "192.168.164.1_".
WARNING: No targets were specified, so 0 hosts scanned.
Nmap done: 0 IP addresses (0 hosts up) scanned in 5.16 seconds
                                           
┌──(fea㉿fea)-[~]
└─$ nmap -sV -sC  -T4 -oN nmap_scan_metasploitable2.txt 192.168.164.254
Starting Nmap 7.98 ( https://nmap.org ) at 2026-05-01 21:58 -0400
Nmap scan report for 192.168.164.254
Host is up (0.00055s latency).
All 1000 scanned ports on 192.168.164.254 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 00:50:56:F1:42:5B (VMware)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 31.18 seconds
                                           
┌──(fea㉿fea)-[~]
└─$ nmap -sV -sC  -T4 -oN nmap_scan_metasploitable2.txt 192.168.164.129
Starting Nmap 7.98 ( https://nmap.org ) at 2026-05-01 21:59 -0400
Nmap scan report for 192.168.164.129
Host is up (0.00092s latency).
Not shown: 977 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 192.168.164.128
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      vsFTPd 2.3.4 - secure, fast, stable
|_End of status
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey: 
|   1024 60:0f:cf:e1:c0:5f:6a:74:d6:90:24:fa:c4:d5:6c:cd (DSA)
|_  2048 56:56:24:0f:21:1d:de:a7:2b:ae:61:b1:24:3d:e8:f3 (RSA)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|_    SSL2_DES_64_CBC_WITH_MD5
|_smtp-commands: metasploitable.localdomain, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN
53/tcp   open  domain      ISC BIND 9.4.2
| dns-nsid: 
|_  bind.version: 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
|_http-title: Metasploitable2 - Linux
|_http-server-header: Apache/2.2.8 (Ubuntu) DAV/2
111/tcp  open  rpcbind     2 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2            111/tcp   rpcbind
|   100000  2            111/udp   rpcbind
|   100003  2,3,4       2049/tcp   nfs
|   100003  2,3,4       2049/udp   nfs
|   100005  1,2,3      35783/tcp   mountd
|   100005  1,2,3      49439/udp   mountd
|   100021  1,3,4      48805/tcp   nlockmgr
|   100021  1,3,4      54044/udp   nlockmgr
|   100024  1          42500/udp   status
|_  100024  1          45177/tcp   status
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login?
514/tcp  open  shell       Netkit rshd
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
| mysql-info: 
|   Protocol: 10
|   Version: 5.0.51a-3ubuntu5
|   Thread ID: 8
|   Capabilities flags: 43564
|   Some Capabilities: Speaks41ProtocolNew, SupportsTransactions, LongColumnFlag, SwitchToSSLAfterHandshake, Support41Auth, SupportsCompression, ConnectWithDatabase
|   Status: Autocommit
|_  Salt: n]gov%RKd5x~2x*e?H/Q
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
| ssl-cert: Subject: commonName=ubuntu804-base.localdomain/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Not valid before: 2010-03-17T14:07:45
|_Not valid after:  2010-04-16T14:07:45
|_ssl-date: 2026-05-02T02:01:48+00:00; +11s from scanner time.
5900/tcp open  vnc         VNC (protocol 3.3)
| vnc-info: 
|   Protocol version: 3.3
|   Security types: 
|_    VNC Authentication (2)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
|_ajp-methods: Failed to get a valid response for the OPTION request
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
|_http-favicon: Apache Tomcat
|_http-title: Apache Tomcat/5.5
|_http-server-header: Apache-Coyote/1.1
MAC Address: 00:0C:29:1C:98:C1 (VMware)
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb-os-discovery: 
|   OS: Unix (Samba 3.0.20-Debian)
|   Computer name: metasploitable
|   NetBIOS computer name: 
|   Domain name: localdomain
|   FQDN: metasploitable.localdomain
|_  System time: 2026-05-01T22:01:08-04:00
|_nbstat: NetBIOS name: METASPLOITABLE, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
|_clock-skew: mean: 1h20m17s, deviation: 2h18m45s, median: 10s
|_smb2-time: Protocol negotiation failed (SMB2)
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 166.46 seconds
                                                              
### acceso MFSD CONSOLE:

<img width="921" height="890" alt="image" src="https://github.com/user-attachments/assets/88dbd1f1-1ee9-4f24-894f-7af72f533740" />
<img width="921" height="410" alt="image" src="https://github.com/user-attachments/assets/e8140537-191d-40d0-be00-e587836e451a" />


### Activacion de Backdoor:

<img width="921" height="365" alt="image" src="https://github.com/user-attachments/assets/ead51f91-cca9-4a09-916d-49091a876056" />


### Configuración de explotacion , del atacante y victima:

<img width="1691" height="421" alt="image" src="https://github.com/user-attachments/assets/8ee003cd-974b-412f-8337-284c73994f33" />

<img width="921" height="102" alt="image" src="https://github.com/user-attachments/assets/82a96334-d531-47ec-aeed-c7a42507846b" />

#### se hace la exploatacion a victima , 192.168.168.129

<img width="1390" height="571" alt="image" src="https://github.com/user-attachments/assets/3284289e-7667-46d0-93e6-64a364fe3a3c" />
<img width="921" height="133" alt="image" src="https://github.com/user-attachments/assets/89894916-ff53-4095-b6c5-e759db7e819a" />
<img width="921" height="274" alt="image" src="https://github.com/user-attachments/assets/841d3dc9-58c9-4b36-8bd8-3ed8fe8d99b1" />

Es todo !

```bash
# Comando ejecutado:
nmap -sV -sC -T4 -oN nmap_scan_metasploitable2.txt 192.168.164.129
