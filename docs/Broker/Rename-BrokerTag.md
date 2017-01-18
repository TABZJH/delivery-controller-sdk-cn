# Rename-BrokerTag

Rename one or more tags.

## 语法

    Rename-BrokerTag [-InputObject] <Tag[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerTag [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Renames one or more tags with the supplied name.

## 相关命令

- [Add-BrokerTag](Add-BrokerTag.html)
- [Get-BrokerTag](Get-BrokerTag.html)
- [New-BrokerTag](New-BrokerTag.html)
- [Remove-BrokerTag](Remove-BrokerTag.html)
- [Set-BrokerTag](Set-BrokerTag.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies one or more tag objects to rename.                                                                                                                                    | true  | true (ByValue)        |                                                                                        |
| 名称           | Identifies tags to be renamed by name.                                                                                                                                          | true  | true (ByPropertyName) |                                                                                        |
| NewName      | Specifies new name for the tags.                                                                                                                                                | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Tag

The tag to rename can be piped into this cmdlet.

## 返回值

### None or Citrix.Broker.Admin.SDK.Tag

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Tag object.## Notes Note that when renaming a tag, its UUID remains the same and any associations are maintained.

## 示例

### 示例 1

    C:\PS> Rename-BrokerTag -Name 'OldName' -NewName 'ReplacementName'
    

Description  
\---\---\-----  
Renames tags with the name 'OldName' to 'ReplacementName'.