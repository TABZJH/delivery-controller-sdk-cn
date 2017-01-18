# Set-BrokerRemotePCAccount

Modify one or more RemotePCAccounts.

## 语法

    Set-BrokerRemotePCAccount [-InputObject] <RemotePCAccount[]> [-PassThru] [-AllowSubfolderMatches <Boolean>] [-MachinesExcluded <String[]>] [-MachinesIncluded <String[]>] [-OU <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Modify one or more RemotePCAccounts.

## 相关命令

- [Get-BrokerRemotePCAccount](Get-BrokerRemotePCAccount.html)
- [New-BrokerRemotePCAccount](New-BrokerRemotePCAccount.html)
- [Remove-BrokerRemotePCAccount](Remove-BrokerRemotePCAccount.html)

## 参数

| 名称                    | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 是否必需？ | 管道输入           | 默认值                                                                                    |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject           | Specifies the RemotePCAccounts to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | true  | true (ByValue) |                                                                                        |
| PassThru              | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | false | false          | False                                                                                  |
| AllowSubfolderMatches | When true a machine matches this RemotePCAccount if the AD computer is in the container specified by the OU property, or within a child container of the OU.  
When false the AD computer object only matches if it is directly in the AD container specified by the OU property.  
This property is not meaningful when OU has the special value 'any'.                                                                                                                                                                                                                                                                                                                                                                                                                              | false | false          |                                                                                        |
| MachinesExcluded      | MachinesExcluded specifies a set of strings that can include asterisk wildcards. If a machine name matches any entries in MachinesExcluded then it cannot match with this RemotePCAccount regardless of whether there is a MachinesIncluded match.  
Matches are performed against the domain name joined with the machine name by a backslash (DOMAIN\MACHINE), e.g.:  
DOMAIN1\M*  
DOMAIN*\M*  
*\M*                                                                                                                                                                                                                                                                                                                                                                           | false | false          |                                                                                        |
| MachinesIncluded      | MachinesIncluded specifies a set of strings that can include asterisk wildcards. A machine may only match with this RemotePCAccount if it matches a MachinesIncluded entry and does not match any MachinesExcluded entries.  
Matches are performed against the domain name joined with the machine name by a backslash (DOMAIN\MACHINE), e.g.:  
DOMAIN1\M*  
DOMAIN*\M*  
*\M*                                                                                                                                                                                                                                                                                                                                                                                                  | false | false          |                                                                                        |
| OU                    | Specifies the DN of an AD container, or has the special value 'any'.  
When an AD container is specified a machine may only match with the RemotePCAccount when the AD computer object is located relative to the OU.  
When 'any' is specified the location of the AD computer object is ignored for purposes of matching this RemotePCAccount. The machine must still meet the MachinesIncluded and MachinesExcluded filters for a match to occur.  
In the event that a machine matches with multiple RemotePCAccounts then the RemotePCAccount OU with the longest canonical name takes precedence. The special 'any' OU is treated as lowest priority.  
Note that the OU value of every RemotePCAccount must be unique, and this includes only one 'any' entry being permitted. | false | false          |                                                                                        |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | false | false          |                                                                                        |
| AdminAddress          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.RemotePCAccount

You can pipe the RemotePCAccounts to be modified into this cmdlet.

## 返回值

### None or Citrix.Broker.Admin.SDK.RemotePCAccount

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.RemotePCAccount object.

## 示例

### 示例 1

    C:\PS> Get-BrokerRemotePCAccount | Set-BrokerRemotePCAccount -MachinesExcluded @('DOMAIN42\*')
    

Description  
\---\---\-----  
Make all RemotePCAccounts filter out machines from DOMAIN42.