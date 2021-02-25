# ** Introduction **

This guide shows how to create an Ignition configuration to deploy a Fedora CoreOS (FCOS) cloud server instance at Vultr. Ignition files are JSON formatted provisioning instructions that configure storage, file systems, systemd units, networks, users, and other items during the first boot of the system. You must supply an Ignition file in the Vultr customer portal when you deploy an FCOS server. The preferred way to create an Ignition file is by transpiling a Fedora CoreOS Configuration (FCC) file with the Fedora CoreOS Config Transpiler, fcct.

## ** Install fcct **

The fcct utility is available for Linux, macOS, and Windows. Windows users may need to install Gpg4win to verify the file signature.

    Download the Fedora signing keys
        $ wget https://getfedora.org/static/fedora.gpg

    Import the keys to gpg.
        $ gpg --import fedora.gpg

    Download the latest version of fcct for your architecture. 
        fcct-x86_64-pc-windows-gnu.exe.asc

    Verify the download.

    $ gpg --verify fcct-x86_64-pc-windows-gnu.exe.asc fcct-x86_64-pc-windows-gnu

    Make the file executable.

    $ chmod +x fcct-x86_64-pc-windows-gnu


## ** Create an FCC File ** 

Fedora CoreOS Configuration (FCC) files are in YAML format. 

    create an example FCC file.
        $ touch example.fcc

    Add Password to Core User
        Generated a SHA512 Hash password
    Set Hostname
        Fedora-host
    Add Private Networking
        10.10.10.10/20
    Create SSH Key on Windows
        cmd -> ssh-keygen

## 3. Transpile FCC to Ignition

The FCC file must be transpiled to Ignition format before use.
    $ ./fcct-x86_64-pc-windows-gnu -o fedora-host.ign fedora-host.fcc
