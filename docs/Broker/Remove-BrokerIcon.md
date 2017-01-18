# Remove-BrokerIcon

Remove an icon.

## 语法

    Remove-BrokerIcon [-InputObject] <Icon[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Removes an icon from the database.

## 相关命令

- [Get-BrokerIcon](Get-BrokerIcon.html)
- [New-BrokerIcon](New-BrokerIcon.html)
- [Set-BrokerIconMetadata](Set-BrokerIconMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the icon to remove.                                                                                                                                                   | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Icon

The icon to be removed can be piped into the cmdlet.

## 返回值

### 无

## Notes Note that if the icon is currently in use, for example, as a desktop icon, it cannot be removed until the association is cleared.

## 示例

### 示例 1

    C:\PS> Remove-BrokerIcon 3
    

Description  
\---\---\-----  
Removes the icon with Uid 3.