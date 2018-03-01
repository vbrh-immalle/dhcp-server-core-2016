# dhcp-server-core-2016
How to install the DHCP feature (with basic configuration) on a Windows Server Core 2016

## Server Core DHCP installation
This README describes the installation of DHCP using Powershell on a Windows Server 2016 core.

## Installation
1. Open powershell through cmd: `powershell`  
2. Use `Install-WindowsFeature` to install DHCP: `Install-WindowsFeature DHCP -IncludeManagementTools`

## Configuration
1. Add a DHCP scope with `Add-DhcpServerv4Scope`, the parameters speak for themselves: `Add-DhcpServerv4Scope -Name "Internal" -StartRange 192.168.1.10 -EndRange 192.168.1.250 -SubnetMask 255.255.255.0 -Description "Scope for the Internal Network"`
2. (optional) configure your server's network adapter configuration with `New-NetIPAddress`. Example: `New-NetIPAddress -InterfaceIndex 7 -IPAddress 192.168.1.1 -PrefixLength 24 -DefaultGateway 192.168.1.1`, to get the correct InterFaceIndex, use `New-NetIPAddress` without any parameters to find the correct Index.
