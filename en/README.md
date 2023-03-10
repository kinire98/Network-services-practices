# Network services
## Resume of the practices table

| Practice | Alternative | Problems | Solutions | Link | Level of pain in the a** (if you go blind) |
| -- | -- | -- | -- | -- | -- |
| **_Practice 0. Network infrastructure_** |  | Problems with graphic interface changing configuration of network interfaces | Change the configuration in the `/etc/network/interfaces` file | [Link to the documentation](./Practice%200.%20Network%20Infrastructure) | 7/10 |
|  |  | Problems with Windows domain | Restart the whole domain |  |  |
|  |  | `/etc/network/interfaces` no working in Xubuntu Server | Change the yaml file of netplan, as specified [here](https://www.ochobitshacenunbyte.com/2021/04/26/netplan-configurar-la-red-en-ubuntu-20-04/). |  |  |
|  |  | The VMWare tools didn't update in Windows 7 | Install Windows 7 Service Pack and a security update, the update the VMWare tools |  |  |
| **_Practice 1. NAT in Windows_** |  | Problem with ranges of the DHCP server | Make the scope serve all the network | [Link to the documentation](./Practice%201.%20NAT%20in%20Windows) | 3/10 |
|  |  | Not starting DHCP for IPv6 | Activate the scope for v6 too, and let VMWare do its thing |  |  |
|  |  | WINS sever disabled (not sure if affects the behaviour of the service) | Use the parameters that VMWare gives the NAT adapter |  |  |
| **_Practice 2. NAT in Linux_** |  | DNS not working in Linux machines | Change them, the ones from Telefónica to the ones from Google | [Link to the documentation](./Practice%202.%20NAT%20in%20Linux) | 3/10 |
|  |  | apt not working in client Ubuntu | Update the OS to a more updated version |  |  |
| **_Practice 3. DHCP server in Windows_** |  | Problem with DNS. I put loopback DNS rather than the address of the DC | Change that parameter in the scope | [Link to the documentation](./Practice%203.%20DHCP%20server%20in%20Windows) | 2/10 |
| **_Practice 4. DHCP server in Linux_** |  | Problems with DNS server restarting | Using the command `/etc/init.d/isc-dhcp-server start` or `/etc/init.d/isc-dchp-server restart` | [Link to the documentation](./Practice%204.%20DHCP%20server%20in%20Linux) | 3/10 |
| **_Practice 5. DHCP server in Windows with 2 scopes_** |  | Not sure how to divide a subnet into two scopes | You can't do that, so instead make two scopes for 2 different subnets | [Link to the documentation](./Practice%205.%20DHCP%20server%20in%20Windows%20with%202%20scopes) | 1/10 |
| **_Practice 6. DHCP server in Linux with 2 scopes_** |  |  |  | [Link to the documentation](./Practice%206.%20DHCP%20server%20in%20Linux%20with%202%20scopes) | 2/10 |
| **_Practice 7. DHCP server in Windows with a Relay Agent_** | I used Windows Server 2012 | Relay Agent send the requests to the DHCP server, but didn't get the response back | Two solutions: <br> <ul> <li>Establish the gateway of the DHCP server to the address of the realy agent (you lose access to the internet)</li> <li>Add a static route to the other subnet</li></ul>  | [Link to the documentation](https://github.com/kinire98/Network-services-practices/tree/main/en/Practice%207.%20DHCP%20server%20in%20Windows%20with%20a%20Relay%20Agent) | 6/10 |
| **_Practice 8. DHCP server in Linux with a Relay Agent_** | I used another Xubuntu Server |  |  | [Link to the documentation](./Practice%208.%20DHCP%20server%20in%20Linux%20with%20a%20Relay%20Agent) | 5/10 |
| **_Practice 9. Install, configure and test telnet and SSH in Windows_** |  | Using telnet command, open firewall y feature installed. But, host couldn't establish the conection even in localhost | Activate telnet service in services | [Link to the documentation](https://github.com/kinire98/Network-services-practices/tree/main/en/Practice%209.%20Install,%20configure%20and%20test%20telnet%20and%20SSH%20in%20Windows) | 7/10 |
|  |  | Two instances of freeSSHd running | Execute the following command in the CMD: `taskkill /F /IM “FreeSSHDService.exe”` and starting freSSHd again |  |  |
| **_Practice 10. Install, configure and test telnet and SSH in Linux_** |  |  |  | [Link to the documentation](./Practice%2010.%20Install,%20configure%20and%20test%20telnet%20and%20SSH%20in%20Linux) | 2/10 |
| **_Practice 11. Install remote desktop in Windows. Test through client app and web browser_** |  |  |  | [Link to the documentation](./Practice%2011.%20Install%20remote%20desktop%20in%20Windows.%20Test%20through%20client%20app%20and%20web%20browser) | 1/10 |
| **_Practice 12. DNS server in Windows with direct and reverse lookup zones with dynamic updates_** |  | Problems with the dynamic updates of the names | Try with a Windows client instead of a Linux one | [Link to the documentation](./Practice%2012.%20DNS%20server%20in%20Windows%20with%20direct%20and%20reverse%20lookup%20zones%20with%20dynamic%20updates) | 3/10 |
| **_Practice 13A. DNS server in Linux with DNSMasq and dynamic updates_** |  | Problems with `/etc/resolv.conf`, because the system service systemd-resolved used the same port and didn't allowed DNSMasq to start | Deactivate systemd-resolved and delete the `/etc/resolv.conf` file | [Link to the documentation](./Practice%2013A.%20DNS%20server%20in%20Linux%20with%20DNSMasq%20and%20dynamic%20updates) | 8.5/10 |
| **_Practice 13B. DNS server in Linux with bind and direct and reverse lookup zones_** |  | Didn't resolved any DNS names, neither internal or external | Reactivate systemd-resolved and in the netplan establish the nameserver to localhost | [Link to the documentation](./Practice%2013B.%20DNS%20server%20in%20Linux%20with%20bind%20and%20direct%20and%20reverse%20lookup%20zones) | 7.5/10 |
| **_Practice 14. Secondary DNS server in Windows_** |  |  |  | [Link to the documentation](./Practice%2014.%20Secondary%20DNS%20server%20in%20Windows) | 7/10 |
| **_Practice 15. Secondary DNS server in Linux_** |  |  |  | [Link to the documentation](./Practice%2015.%20Secondary%20DNS%20server%20in%20Linux) | 9/10 |
| **_Practice 16. Create a subdomain in Windows not integrated in Active Directory and delegate its administration_** |  | Problem delegating the inverse lookup zones | Create the zone for 1.10 and delegate 19.1.10 | [Link to the documentation](./Practice%2016.%20Create%20a%20subdomain%20in%20Windows%20not%20integrated%20in%20Active%20Directory) | 9/10 |
| **_Practice 17. Create a subdomain in Linux and delegate its administration_** |  |  |  | [Link to the documentation](./Practice%2017.%20Create%20a%20subdomain%20in%20Linux%20and%20delegate%20its%20administration) | 10/10 |
| **_Practice 18A. Create an FTP server in Windows with IIS_** |  |  |  | [Link to the documentation](./Practice%2018A.%20Create%20an%20FTP%20server%20in%20Windows%20with%20IIS) | 7.5/10 |
| **_Practice 18B. Try the FTP encrypted protocol in Windows with IIS (FTPS)_** |  | Client connects but but it timesout and server never validates the credentials | Create FTP site in port 21 -> Allow conecction SSL. Then, you go to certifcates and select self-signed certificate | [Link to the documentation](./Practice%2018B.%20Try%20the%20FTP%20encrypted%20protocol%20in%20Windows%20with%20IIS%20(SFTP%20o%20FTPS)) | 10/10 |
| **_Practice 19A. Make an FTP server in linux with proftpd_** |  |  |  | [Link to the documentation](./Practice%2019A.%20Make%20an%20FTP%20server%20in%20linux%20with%20proftpd) | 1/10 |
| **_Practice 19B. Try the FTP encrypted protocol in Linux (SFTP)_** |  |  |  |  [Link to the documentation](./Practice%2019B.%20Try%20the%20FTP%20encrypted%20protocol%20in%20Linux%20(SFTP)) | 2/10 |
| **_Practice 20A. Web server in Windows with IIS_** |  | It appeared the default web for IIS | Disable the default site | [Link to the documentation](./Practice%2020A.%20Web%20server%20in%20Windows%20with%20IIS) | 6/10 |
| **_Practice 20B. Create a virtual host in the 8080 port_** |  |  |  | [Link to the documentation](./Practice%2020B.%20Create%20a%20virtual%20host%20in%20the%208080%20port) | 1/10 |
| **_Practice 20C. Access to safe folders with HTTPS_** |  |  |  | [Link to the documentation](./Practice%2020C.%20Access%20to%20safe%20folders%20with%20HTTPS) | 1/10 |
| **_Practice 20D. Protección of base folders_** |  |  |  | [Link to the documentation](./Practice%2020D.%20Protección%20of%20base%20folders) | 1/10 |
| **_Practice 20E. PHP + MySQL + PHPMyAdmin_** |  |  |  | [Link to the documentation](./Practice%2020E.%20PHP%20+%20MySQL%20+%20PHPMyAdmin) | 1/10 |
| **_Practice 21A. Web server in Linux with Apache_** |  |  |  | [Link to the documentation](./Practice%2021A.%20Web%20server%20in%20Linux%20with%20Apache) | 3.5/10 |
| **_Practice 21B. Make users folders_** |  |  |  | [Link to the documentation](./Practice%2021B.%20Make%20users%20folders) | 4.5/10 |
| **_Practice 21C. Virtual host by IP address_** |  |  |  | [Link to the documentation](./Practice%2021C.%20Virtual%20host%20by%20IP%20address) | 4.5/10 |
| **_Practice 21D. Safe folders with HTTPS_** |  |  |  | [Link to the documentation](./Practice%2021D.%20Safe%20folders%20with%20HTTPS) | 4.5/10 |
| **_Practice 21E. Private folders access_** |  |  |  | [Link to the documentation](./Practice%2021E.%20Private%20folders%20access) | 4.5/10 |
| **_Practice 21F. PHP + MySQL + PHPMyAdmin_** |  |  |  | [Link to the documentation](./Practice%2021F.%20PHP%20+%20MySQL%20+%20PHPMyAdmin) | 8/10 |
| **_Practice 22. E-mail server in Windows with IIS_** |  |  |  | [Link to the documentation](./Practice%2022.%20E-mail%20server%20in%20Windows%20with%20IIS) | 6/10 |
| **_Practice 23. E-mail server in Linux with postfix, dovecot, squirrelmail and Thunderbird_** |  |  |  | [Link to the documentation](./Practice%2023.%20E-mail%20server%20in%20Linux%20with%20postfix,%20dovecot%20and%20squirrelmail) | 12/10 | 
| **_Practice 24. Make a forum server in Windows with PHPBB_** |  |  |  | [Link to the documentation](./Practice%2024.%20Make%20a%20forum%20server%20in%20Windows%20with%20PHPBB) | 2/10 |
| **_Practice 25. Make a forum server in Linux with PHPBB_** |  |  |  | [Link to the documentation](./Practice%2025.%20Make%20a%20forum%20server%20in%20Linux%20with%20PHPBB) | 1/10 |
| **_Practice 26. Instant messaging server with ejabberd_** |  |  |  | [Link to the documentation](./Practice%2026.%20Instant%20messaging%20server%20with%20ejabberd) | 9.5/10 |
| **_Practice 27. Video streaming server with VLC_** |  |  |  | [Link to the documentation](./Practice%2027.%20Video%20streaming%20server%20with%20VLC) | 7.5/10 |
| **_Practice 28. Videoconference server in Linux with GNUGK_** |  | NOTE: Doesn't work |  | [Link to the documentation](./Practice%2028.%20Videoconference%20server%20in%20Linux%20with%20GNUGK) | 15/10 |
| **_Practice 29. Transition from IPv4 to IPv6 with an ISATAP tunnel_** |  |  |  | [Link to the documentation](./Practice%2029%20Transition%20from%20IPv4%20to%20IPv6%20with%20an%20ISATAP%20tunnel) | 3/10 |
| **_Practice 30. Double network stack in PacketTracert_** |  |  |  | [Link to the documentation](./Practice%2030.%20Double%20network%20stack%20in%20PacketTracert) | 7/10 (It's not that difficult, I just don't like PacketTracert) |
| **_Practice 31. 6to4 tunnel. GNS3_** |  | Note: This might be a tricky one, because GNS3 is a free program, but for the IOS to make the virtual router work you have to pay for it |  | [Link to the documentation](./Practice%2031.%206to4%20tunnel.%20GNS3) | 4/10 |
| **_Practice 32. Remote Desktop through SSH tunnel_** |  |  |  | [Link to the documentation](./Practice%2032.%20Remote%20Desktop%20through%20SSH%20tunnel) | 1/10 |
| **_Practice 33. DHCP Failover_** |  |  |  | [Link to the documentation](./Practice%2033.%20DHCP%20Failover) | 4/10 |

