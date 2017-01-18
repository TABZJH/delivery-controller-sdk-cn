# Remove-BrokerConfigurationSlot

Removes a configuration slot.

## 语法

    Remove-BrokerConfigurationSlot [-InputObject] <ConfigurationSlot[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerConfigurationSlot [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Removes a configuration slot from the site. All machine configurations associated with this slot are also removed.

## 相关命令

- [New-BrokerConfigurationSlot](New-BrokerConfigurationSlot.html)
- [Get-BrokerConfigurationSlot](Get-BrokerConfigurationSlot.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Configuration slot to remove.                                                                                                                                                   | true  | true (ByValue)        |                                                                                        |
| 名称           | Name of configuration slot to remove.                                                                                                                                           | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Configuration slot to remove

Configuration slots may be specified through pipeline input.

## 返回值

### 无

## 示例

### 示例 1

    Remove-BrokerConfigurationSlot -Name "User Profile Manager"
    

Description  
\---\---\-----  
Remove the configuration slot named "User Profile Manager".