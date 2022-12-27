# Building Matter

## Building Matter

*   In the WSL terminal use the following command to clone the project, and run the following command to sync the submodule:

    {% code title="Shell" %}
    ```
    $ git clone --recurse-submodules https://github.com/RexhuangTW/connectedhomeip.git
    $ cd connectedhomeip
    $ git submodule update --init
    ```
    {% endcode %}
* To get started select "Open folder..." to open "connectedhomeip" folder

***

## Setup environment (in Remote WSL)

#### Install VSCode extension

* Install all recommendations tools:
  * spmeesseman.vscode-taskexplorer
  * ms-vscode.cpptools
  * ms-vscode-remote.remote-containers
  * ms-azuretools.vscode-docker
  * dan-c-underwood.arm
  * twxs.cmake
  * vadimcn.vscode-lldb
  * marus25.cortex-debug

#### Setup Rafael Matter Docker

* Run VSCode task: "RT matter dev setup" Task "RT matter dev setup" include three sub-task:

1. "RT matter image build (Step I)"
2. "RT matter container build (Step II)"
3. "RT matter container env setup (Step III)"

#### Building project

* NOTE: When the first time building, Matter will setup the matter environment (GCC toolchain, Python, GN)
* Run VSCode task: "Build RT lighting example"
