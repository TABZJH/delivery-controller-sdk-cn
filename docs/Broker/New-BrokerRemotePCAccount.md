# New-BrokerRemotePCAccount

Create a new RemotePCAccount.

## 语法

    New-BrokerRemotePCAccount -CatalogUid <Int32> -OU <String> [-AllowSubfolderMatches <Boolean>] [-MachinesExcluded <String[]>] [-MachinesIncluded <String[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Create a new RemotePCAccount. A RemotePCAccount defines machine filters to support Remote PC automation adding unconfigured machines to catalogs.

## 相关命令

- [Get-BrokerRemotePCAccount](Get-BrokerRemotePCAccount.html)
- [Set-BrokerRemotePCAccount](Set-BrokerRemotePCAccount.html)
- [Remove-BrokerRemotePCAccount](Remove-BrokerRemotePCAccount.html)

## 参数

| 名称                    | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| CatalogUid            | Specifies the catalog which Remote PC automation adds an unconfigured machine to if it matches this RemotePCAccount.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | true  | true (ByPropertyName) |                                                                                        |
| OU                    | Specifies the DN of an AD container, or has the special value 'any'.  
When an AD container is specified a machine may only match with the RemotePCAccount when the AD computer object is located relative to the OU.  
When 'any' is specified the location of the AD computer object is ignored for purposes of matching this RemotePCAccount. The machine must still meet the MachinesIncluded and MachinesExcluded filters for a match to occur.  
In the event that a machine matches with multiple RemotePCAccounts then the RemotePCAccount OU with the longest canonical name takes precedence. The special 'any' OU is treated as lowest priority.  
Note that the OU value of every RemotePCAccount must be unique, and this includes only one 'any' entry being permitted. | true  | true (ByPropertyName) | 空值                                                                                     |
| AllowSubfolderMatches | When true a machine matches this RemotePCAccount if the AD computer object exists within the container specified by the OU property, or within a child container of the OU.  
When false the AD computer object only matches if it exists directly in the AD container specified by the OU property.  
This property is not meaningful when OU has the special value 'any'.                                                                                                                                                                                                                                                                                                                                                                                                           | false | true (ByPropertyName) | false                                                                                  |
| MachinesExcluded      | MachinesExcluded specifies a set of strings that can include asterisk wildcards. If a machine name matches any entries in MachinesExcluded then it cannot match with this RemotePCAccount regardless of whether there is a MachinesIncluded match.  
Matches are performed against the domain name joined with the machine name by a backslash (DOMAIN\MACHINE), e.g.:  
DOMAIN1\M*  
DOMAIN*\M*  
*\M*                                                                                                                                                                                                                                                                                                                                                                           | false | true (ByPropertyName) | @()                                                                                    |
| MachinesIncluded      | MachinesIncluded specifies a set of strings that can include asterisk wildcards. A machine may only match with this RemotePCAccount if it matches a MachinesIncluded entry and does not match any MachinesExcluded entries.  
Matches are performed against the domain name joined with the machine name by a backslash (DOMAIN\MACHINE), e.g.:  
DOMAIN1\M*  
DOMAIN*\M*  
*\M*                                                                                                                                                                                                                                                                                                                                                                                                  | false | true (ByPropertyName) | @('*')                                                                                 |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | false | false                 |                                                                                        |
| AdminAddress          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.RemotePCAccount

The newly created RemotePCAccount.

## 示例

### 示例 1

    C:\PS> New-BrokerRemotePCAccount -OU 'ou=MyOU,dc=MyDomain,dc=com' -CatalogUid 42
    

Description  
\---\---\-----  
Create a RemotePCAccount that adds unconfigured machines with computer objects in MyOU, into catalog 42.

### 示例 2

    C:\PS> New-BrokerRemotePCAccount -OU 'any' -CatalogUid 42 -MachinesIncluded @('DOMAIN1\*') -MachinesExcluded @('DOMAIN1\*JOHNDOE*')
    

Description  
\---\---\-----  
Create a RemotePCAccount matching unconfigured machines from DOMAIN1, except those with hostnames containing JOHNDOE, and add them to catalog 42.

### 示例 3

    C:\PS> New-BrokerRemotePCAccount -OU 'any' -CatalogUid 42
    

Description  
\---\---\-----  
Create a RemotePCAccount that matches any unconfigured machine, causing automation to add matching machines to catalog 42.