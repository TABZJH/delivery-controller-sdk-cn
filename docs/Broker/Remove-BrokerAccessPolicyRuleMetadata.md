# Remove-BrokerAccessPolicyRuleMetadata

Deletes AccessPolicyRule Metadata from the AccessPolicyRule objects

## 语法

    Remove-BrokerAccessPolicyRuleMetadata [-InputObject] <AccessPolicyRule[]> -Name <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerAccessPolicyRuleMetadata cmdlet deletes Metadata from the AccessPolicyRule objects.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the AccessPolicyRule object's instance whose Metadata is to be deleted.                                                                                               | true  | true (ByValue) |                                                                                        |
| 名称           | Specifies the name of the Metadata to be deleted                                                                                                                                | true  | false          |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.BrokerAccessPolicyRule

You can pipe the AccessPolicyRule to delete the metadata.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerAccessPolicyRuleMetadata -InputObject $obj-Uid -Name "MyMetadataName"
    

Description  
\---\---\-----  
This command deletes the Metadata "MyMetadataName" key-value pair for the AccessPolicyRule whose instance is pointed by $obj-Uid

### 示例 2

    C:\PS> Get-BrokerAccessPolicyRule | Remove-BrokerAccessPolicyRuleMetadata -Name "MyMetadataName"
    

Description  
\---\---\-----  
This command deletes the Metadata "MyMetadataName" key-value pair for all the AccessPolicyRule in the site