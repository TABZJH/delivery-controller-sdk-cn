# Set-BrokerTag

Sets the properties of a tag.

## 语法

    Set-BrokerTag [-InputObject] <Tag[]> [-PassThru] [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerTag [-Name] <String> [-PassThru] [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerTag cmdlet sets properties of a tag or set of tags. The tags on which to operate can be specified by name, in which case multiple tags may be specified through the use of wildcards, or by passing one or more Tag instances to the cmdlet by piping or by using the -InputObject parameter.

## 相关命令

- [Add-BrokerTag](Add-BrokerTag.html)
- [Get-BrokerTag](Get-BrokerTag.html)
- [New-BrokerTag](New-BrokerTag.html)
- [Remove-BrokerTag](Remove-BrokerTag.html)
- [Rename-BrokerTag](Rename-BrokerTag.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the tag objects to modify.                                                                                                                                            | true  | true (ByValue)        |                                                                                        |
| 名称           | Identifies the tag to modify.                                                                                                                                                   | true  | true (ByPropertyName) |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| 说明           | Supplies the new value of the Description property.                                                                                                                             | false | false                 |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Tag

You can pipe the tags to be modified to Set-BrokerTag.

## 返回值

### None or Citrix.Broker.Admin.SDK.Tag

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Tag object.## Notes A tag's Name property cannot be changed by Set-BrokerTag. To rename a tag use Rename-BrokerTag.

## 示例

### 示例 1

    C:\PS> $mytag = Get-BrokerTag MyTag
    C:\PS> Set-BrokerTag -InputObject $mytag -Description "This is my tag. I use it to label all my things."
    

Description  
\---\---\-----  
This example sets the description for the existing tag MyTag.