# Rename-BrokerApplicationGroup

Renames an application group.

## 语法

    Rename-BrokerApplicationGroup [-InputObject] <ApplicationGroup[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerApplicationGroup [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerApplicationGroup cmdlet changes the name of an application group. An application group cannot have the same name as another application group.

Application group names are not visible to end users.

## 相关命令

- [Add-BrokerApplicationGroup](Add-BrokerApplicationGroup.html)
- [Get-BrokerApplicationGroup](Get-BrokerApplicationGroup.html)
- [New-BrokerApplicationGroup](New-BrokerApplicationGroup.html)
- [Remove-BrokerApplicationGroup](Remove-BrokerApplicationGroup.html)
- [Set-BrokerApplicationGroup](Set-BrokerApplicationGroup.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the application group to rename.                                                                                                                                      | true  | true (ByValue)        | nul                                                                                    |
| 名称           | Specifies the name of the application group to rename.                                                                                                                          | true  | true (ByPropertyName) | 空值                                                                                     |
| NewName      | Specifies the new name of the application group.                                                                                                                                | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.ApplicationGroup

You can pipe application groups to Rename-BrokerApplicationGroup.

## 返回值

### None or Citrix.Broker.Admin.SDK.ApplicationGroup

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.ApplicationGroup object.

## 示例

### 示例 1

    C:\PS> Rename-BrokerApplicationGroup -Name "Ofice" -NewName "Office"
    

Description  
\---\---\-----  
Renames the application group with name "Ofice" to "Office".

### 示例 2

    C:\PS> Get-BrokerApplicationGroup -Uid 1 | Rename-BrokerApplicationGroup -NewName "New Name" -PassThru
    

Description  
\---\---\-----  
Renames application group with the Uid 1 to "New Name", showing the result.