# Remove-BrokerPowerTimeSchemeMetadata

Deletes PowerTimeScheme Metadata from the PowerTimeScheme objects

## 语法

    Remove-BrokerPowerTimeSchemeMetadata [-InputObject] <PowerTimeScheme[]> -Name <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerPowerTimeSchemeMetadata cmdlet deletes Metadata from the PowerTimeScheme objects.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the PowerTimeScheme object's instance whose Metadata is to be deleted.                                                                                                | true  | true (ByValue) |                                                                                        |
| 名称           | Specifies the name of the Metadata to be deleted                                                                                                                                | true  | false          |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.BrokerPowerTimeScheme

You can pipe the PowerTimeScheme to delete the metadata.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerPowerTimeSchemeMetadata -InputObject $obj-Uid -Name "MyMetadataName"
    

Description  
\---\---\-----  
This command deletes the Metadata "MyMetadataName" key-value pair for the PowerTimeScheme whose instance is pointed by $obj-Uid

### 示例 2

    C:\PS> Get-BrokerPowerTimeScheme | Remove-BrokerPowerTimeSchemeMetadata -Name "MyMetadataName"
    

Description  
\---\---\-----  
This command deletes the Metadata "MyMetadataName" key-value pair for all the PowerTimeScheme in the site