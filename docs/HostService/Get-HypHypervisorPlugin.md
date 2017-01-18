# Get-HypHypervisorPlugin

Gets the available hypervisor types.

## 语法

    Get-HypHypervisorPlugin [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to retrieve a list of all the available hypervisor types, and their localized names.

## 相关命令

- [New-Item](New-Item.html)

## 参数

| 名称           | 说明                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | ----- | ------------------------------------- |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide this as a host name or an IP address. | false | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Host.Sdk.HypervisorPlugin  
Get-HypHypervisorPlugin returns a list of objects containing the definition of the hypervisor plug-ins.  
ConnectionType <Citrix.XDInterServiceTypes.ConnectionType>  
The hypervisor connection type. This can be one of the following:  
XenServer - XenServer hypervisor  
SCVMM - Microsoft SCVMM/Hyper-V  
vCenter - VMWare vSphere/ESX  
Custom - a third-party hypervisor  
DisplayName <string>  
The localized display name (localized using the locale of the Powershell snap-in session)  
PluginFactoryName <string>  
The name of the hypervisor plug-in factory used to manage the hypervisor connections.

## Notes To use third-party plug-ins, the plug-in assemblies must be installed into the appropriate location on each controller machine that forms part of the Citrix controller site. Failure to do this can result in unpredictable behavior, especially during service failover conditions.  
In the case of failure the following errors can result.  
Error Codes  
\---\---\-----  
DatabaseError  
An error occurred in the service while attempting a database operation.  
CommunicationError  
An error occurred while communicating with the service.  
InvalidFilter  
A filtering expression was supplied that could not be interpreted for this cmdlet.  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    c:\PS> Get-HypHypervisorPlugin | Format-Table -AutoSize
    
              ConnectionType DisplayName              PluginFactoryName
              -------------- -----------              -----------------
                       SCVMM Microsoft virtualization MicrosoftPSFactory
                     VCenter VMware virtualization    VmwareFactory
                   XenServer Citrix XenServer         XenFactory
    

Description  
\---\---\-----  
Get the available hypervisor management plug-ins.