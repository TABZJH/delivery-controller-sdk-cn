# New-BrokerHypervisorConnection

Creates a new hypervisor connection.

## 语法

    New-BrokerHypervisorConnection [-HypHypervisorConnectionUid] <Guid> [-PreferredController <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The New-BrokerHypervisorConnection cmdlet creates a new hypervisor connection.

## 相关命令

- [Get-BrokerHypervisorConnection](Get-BrokerHypervisorConnection.html)
- [Remove-BrokerHypervisorConnection](Remove-BrokerHypervisorConnection.html)
- [Set-BrokerHypervisorConnection](Set-BrokerHypervisorConnection.html)

## 参数

| 名称                         | 说明                                                                                                                                                                                                                                                                                                                                                                      | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| HypHypervisorConnectionUid | The Guid that identifies the hypervisor connection, as defined in DUM.                                                                                                                                                                                                                                                                                                  | true  | true (ByPropertyName) |                                                                                        |
| PreferredController        | The preferred controller machine for the hypervisor connection. Can be specified as (first match is used):  
o Full SAM name.  
o Full DNS name.  
o SID value.  
o NetBIOS name (SAM without domain).  
o Partial DNS name (DNS name without some or all domain information).  
Where not specified, the system selects preferred controller machine based on loading. | false | true (ByPropertyName) |                                                                                        |
| LoggingId                  | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                         | false | false                 |                                                                                        |
| AdminAddress               | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                      | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

## 返回值

### Citrix.Broker.Admin.SDK.HypervisorConnection

New-BrokerHypervisorConnection returns an opaque object containing information about the hypervisor connection.

## 示例

### 示例 1

    C:\PS> New-BrokerHypervisorConnection -PreferredController "domainName\controllerName" -HypHypervisorConnectionUid "d16f4e56-b85e-4ba6-b745-0e978ae4f192"
    

Description  
\---\---\-----  
This command creates a new hypervisor connection with a preferred controller.

### 示例 2

    C:\PS> New-BrokerHypervisorConnection -HypHypervisorConnectionUid "d16f4e56-b85e-4ba6-b745-0e978ae4f192"
    

Description  
\---\---\-----  
This command creates a new hypervisor connection, and leaves it to the system to select a preferred controller.