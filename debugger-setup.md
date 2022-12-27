# Debugger setup

### Pre-request

* SEGGER JLink: [Download](https://www.segger.com/downloads/jlink/)

### Setup Network connection between windows and WSL2

* Windows should accept WSL to access the host network, so we need to set up the FireWall setting with "PowerShell administrator"

{% code title="PowerShell administrator" %}
```
$ New-NetFirewallRule -DisplayName "WSL" -Direction Inbound -InterfaceAlias "vEthernet (WSL)" -Action Allow
```
{% endcode %}

*   WSL we need setup a host IP's environment variable for VScode to debug scripts

    * \~/.bashrc add the following setting:

    {% code title="Shell" %}
    ```
    $ sudo <your_text_editor> ~/.bashrc
    $ export WSL_HOST_IP=$(cat /etc/resolv.conf | sed -rn 's|nameserver (.*)|\1|p')
    ```
    {% endcode %}

    * Apply those setting:

    {% code title="Shell" %}
    ```
    $ source ~/.bashrc
    ```
    {% endcode %}

    * Install some packages for the debugger

    {% code title="Shell" %}
    ```
    $ sudo apt-get update
    $ sudo apt-get install libncurses5
    ```
    {% endcode %}

{% hint style="info" %}
Close all Vscode window, and reopen it (This action will help VScode apply the WSL's environment values)
{% endhint %}

### Setup Configure

* Add Rafael's configure file to JLink:
  * Append JLinkDevices.xml and RT58x\_1MB.FLM to JLink path (ex:C:\Program Files (x86)\SEGGER\JLink)
* Config VSCode debugger setup (task.json):
  * From Task launchJLink "label": "launchJLink"
    * JLink setup : replace command \<JLinkGDBServerCL.exe path>, ex: /mnt/c/Program Files (x86)/SEGGER/JLink/JLinkGDBServerCL.exe ( in WSL C:/ should change to /mnt/c/)

{% hint style="info" %}
Note: This debugger's Arm Toolchain and execute file will use matter code and decker env, so you need setup matter env before the debugger
{% endhint %}

<figure><img src=".gitbook/assets/debugger.png" alt=""><figcaption></figcaption></figure>

***

### Start Debugger
