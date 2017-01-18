# Remove-BrokerImportedFTA

Deletes one or more imported file type associations.

## 语法

    Remove-BrokerImportedFTA -DesktopGroupUids <Int32[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Deletes all of the imported file type associations belonging to one or more desktop groups. At least one desktop group must be specified.

Imported file type associations are grouped together based on the desktop group of the machine from which they were imported. All file types for a desktop group are deleted. There is no mechanism for deleting a subset imported file type associations for a specific desktop group.

Imported file type associations are different from configured file type associations. Imported file type associations are lists of known file type associations for a given desktop group. Configured file type associations are those that are actually associated with published applications for the purposes of content redirection.

## 相关命令

- [Get-BrokerImportedFTA](Get-BrokerImportedFTA.html)
- [Update-BrokerImportedFTA](Update-BrokerImportedFTA.html)

## 参数

| 名称               | 说明                                                                                                                                                                              | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| DesktopGroupUids | Deletes the imported file type associations belonging to specified desktop groups.                                                                                              | true  | false |                                                                                        |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                                                                        |
| AdminAddress     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Int32[]

An array of Uids for the desktop groups can be supplied as input. The desktop groups must be of the Private or Shared desktop kind.

## 返回值

### 无

## Notes If an imported file type association is used to create a new configured file type association and the imported file type association is subsequently deleted, the configured file type association is not affected.

## 示例

### 示例 1

    C:\PS> $dg = Get-BrokerDesktopGroup -Name "Sales VMs"
    C:\PS> Remove-BrokerImportedFTA -DesktopGroupUids $dg.Uid
    

Description  
\---\---\-----  
Deletes all imported file type associations belonging to the "Sales VMs" desktop group.