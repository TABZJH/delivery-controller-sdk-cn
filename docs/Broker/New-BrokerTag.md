# New-BrokerTag

Creates a new tag.

## 语法

    New-BrokerTag [-Name] <String> [-Description <String>] [-UUID <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Creates a tag that can be associated with other objects using Add-BrokerTag.

## 相关命令

- [Add-BrokerTag](Add-BrokerTag.html)
- [Get-BrokerTag](Get-BrokerTag.html)
- [Remove-BrokerTag](Remove-BrokerTag.html)
- [Rename-BrokerTag](Rename-BrokerTag.html)
- [Set-BrokerTag](Set-BrokerTag.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| 名称           | Specifies a name for the new tag.                                                                                                                                               | true  | true (ByPropertyName) |                                                                                        |
| 说明           | A description for the tag.                                                                                                                                                      | false | true (ByPropertyName) |                                                                                        |
| UUID         | Specifies a UUID for the new tag. When not specified, a UUID is automatically assigned.                                                                                         | false | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

Input cannot be piped to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.Tag

Outputs the generated tag.

## 示例

### 示例 1

    C:\PS> New-BrokerTag -Name 'Tag1'
    

Description  
\---\---\-----  
Creates a new tag with name 'Tag1'.

### 示例 2

    C:\PS> New-BrokerTag 'Tag2' | Add-BrokerTag -Machine DOMAIN\Machine
    

Description  
\---\---\-----  
Creates a new tag with name 'Tag2' and associates it with machine DOMAIN\Machine.