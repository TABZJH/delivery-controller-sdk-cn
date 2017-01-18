# Rename-BrokerAccessPolicyRule

Renames a rule in the site's access policy.

## 语法

    Rename-BrokerAccessPolicyRule [-InputObject] <AccessPolicyRule[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerAccessPolicyRule [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerAccessPolicyRule cmdlet renames a rule in the site's access policy. The Name property of the rule is changed.

An access policy rule defines a set of connection filters and access control rights relating to a desktop group. These allow fine-grained control of what access is granted to a desktop group based on details of, for example, a user's endpoint device, its address, and the user's identity.

## 相关命令

- [New-BrokerAccessPolicyRule](New-BrokerAccessPolicyRule.html)
- [Get-BrokerAccessPolicyRule](Get-BrokerAccessPolicyRule.html)
- [Set-BrokerAccessPolicyRule](Set-BrokerAccessPolicyRule.html)
- [Remove-BrokerAccessPolicyRule](Remove-BrokerAccessPolicyRule.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The access policy rule to be renamed.                                                                                                                                           | true  | true (ByValue)        |                                                                                        |
| 名称           | The existing name of the access policy rule to be renamed.                                                                                                                      | true  | true (ByPropertyName) |                                                                                        |
| NewName      | The new name for the access policy rule being renamed. The new name must not match that of any other existing rules in the policy.                                              | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.AccessPolicyRule

The access policy rule to be renamed.

## 返回值

### None or Citrix.Broker.Admin.SDK.AccessPolicyRule

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AccessPolicyRule object.

## 示例

### 示例 1

    C:\PS> Rename-BrokerAccessPolicyRule 'Sales' -NewName 'TeleSales'
    

Description  
\---\---\-----  
Renames the access policy rule called Sales to TeleSales. The new name of the rule must be unique in the access policy.