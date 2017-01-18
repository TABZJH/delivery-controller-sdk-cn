# Remove-BrokerSiteMetadata

Deletes Site Metadata from the Site objects

## 语法

    Remove-BrokerSiteMetadata -Name <String> [[-InputObject] <Site[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerSiteMetadata cmdlet deletes Metadata from the Site objects.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| 名称           | Specifies the name of the Metadata to be deleted                                                                                                                                | true  | false          |                                                                                        |
| InputObject  | Specifies the Site object's instance whose Metadata is to be deleted.                                                                                                           | false | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.BrokerSite

You can pipe the Site to delete the metadata.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerSiteMetadata -Name "MyMetadataName"
    

Description  
\---\---\-----  
This command deletes the Metadata "MyMetadataName" key-value pair for the Site