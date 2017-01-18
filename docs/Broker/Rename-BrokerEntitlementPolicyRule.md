# Rename-BrokerEntitlementPolicyRule

Renames a desktop rule in the site's entitlement policy.

## 语法

    Rename-BrokerEntitlementPolicyRule [-InputObject] <EntitlementPolicyRule[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerEntitlementPolicyRule [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerEntitlementPolicyRule cmdlet renames a desktop rule in the site's entitlement policy. The Name property of the rule is changed.

A desktop rule in the entitlement policy defines the users who are allowed per-session access to a machine from the rule's associated desktop group to run a full desktop session.

## 相关命令

- [New-BrokerEntitlementPolicyRule](New-BrokerEntitlementPolicyRule.html)
- [Get-BrokerEntitlementPolicyRule](Get-BrokerEntitlementPolicyRule.html)
- [Set-BrokerEntitlementPolicyRule](Set-BrokerEntitlementPolicyRule.html)
- [Remove-BrokerEntitlementPolicyRule](Remove-BrokerEntitlementPolicyRule.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                 | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The desktop rule in the entitlement policy to be renamed.                                                                                                                                                          | true  | true (ByValue)        |                                                                                        |
| 名称           | The existing name of the desktop rule in the entitlement policy to be renamed.                                                                                                                                     | true  | true (ByPropertyName) |                                                                                        |
| NewName      | The new name of the desktop rule in the entitlement policy being renamed. The new name must not match that of any other existing rule in the policy (irrespective of whether it is a desktop or application rule). | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                     | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                    | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                 | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.EntitlementPolicyRule

The desktop rule in the entitlement policy being renamed.

## 返回值

### None or Citrix.Broker.Admin.SDK.EntitlementPolicyRule

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.EntitlementPolicyRule object.

## 示例

### 示例 1

    C:\PS> Rename-BrokerEntitlementPolicyRule 'Prod Dev' -NewName 'Product Development'
    

Description  
\---\---\-----  
Renames the desktop rule in the entitlement policy called Prod Dev to Product Development. The new name of the rule must be unique in the entitlement policy.