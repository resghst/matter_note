# Setup your WSL network to access the debugger

## Setup your WSL network to access the debugger

*   Make sure your vEthernet (WSL) is in the IP list:

    {% code title="PowerShell " %}
    ```
    ipconfig

    Windows IP 設定
    乙太網路卡 乙太網路 2:
    連線特定 DNS 尾碼 . . . . . . . . : smb.com
    連結-本機 IPv6 位址 . . . . . . . : fe80::c87:726a:2015:4915%15
    IPv4 位址 . . . . . . . . . . . . : 192.168.1.29
    子網路遮罩 . . . . . . . . . . . .: 255.255.255.0
    預設閘道 . . . . . . . . . . . . .: 192.168.1.254
    乙太網路卡 vEthernet (WSL):
    連線特定 DNS 尾碼 . . . . . . . . :
    連結-本機 IPv6 位址 . . . . . . . : fe80::cc59:52d8:9dda:62f2%35
    IPv4 位址 . . . . . . . . . . . . : 172.18.224.1
    子網路遮罩 . . . . . . . . . . . .: 255.255.240.0
    ```
    {% endcode %}
*   Using admin PowerShell execute: (This command run with administrator PowerShell)

    {% code title="PowerShell (Administrator)" %}
    ```
    New-NetFirewallRule -DisplayName "WSL" -Direction Inbound -InterfaceAlias "vEthernet (WSL)" -
    ```
    {% endcode %}
