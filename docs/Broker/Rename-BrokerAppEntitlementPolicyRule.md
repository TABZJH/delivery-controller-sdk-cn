# Rename-BrokerAppEntitlementPolicyRule

Renames an application rule in the site's entitlement policy.

## 语法

    Rename-BrokerAppEntitlementPolicyRule [-InputObject] <AppEntitlementPolicyRule[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerAppEntitlementPolicyRule [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerAppEntitlementPolicyRule cmdlet renames an application rule in the site's entitlement policy. The Name property of the rule is changed.

An application rule in the entitlement policy defines the users who are allowed per-session access to a machine to run one or more applications published from the rule's desktop group.

## 相关命令

- [New-BrokerAppEntitlementPolicyRule](New-BrokerAppEntitlementPolicyRule.html)
- [Get-BrokerAppEntitlementPolicyRule](Get-BrokerAppEntitlementPolicyRule.html)
- [Set-BrokerAppEntitlementPolicyRule](Set-BrokerAppEntitlementPolicyRule.html)
- [Remove-BrokerAppEntitlementPolicyRule](Remove-BrokerAppEntitlementPolicyRule.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The application rule in the entitlement policy to be renamed.                                                                                                                                                          | true  | true (ByValue)        |                                                                                        |
| 名称           | The existing name of the application rule in the entitlement policy to be renamed.                                                                                                                                     | true  | true (ByPropertyName) |                                                                                        |
| NewName      | The new name of the application rule in the entitlement policy being renamed. The new name must not match that of any other existing rule in the policy (irrespective of whether it is a desktop or application rule). | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                         | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                        | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                     | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.AppEntitlementPolicyRule

The application rule in the entitlement policy being renamed.

## 返回值

### None or Citrix.Broker.Admin.SDK.AppEntitlementPolicyRule

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AppEntitlementPolicyRule object.

## 示例

### 示例 1

    C:\PS> Rename-BrokerAppEntitlementPolicyRule 'Prod Dev' -NewName 'Product Development'
    

Description  
\---\---\-----  
Renames the application rule in the entitlement policy called Prod Dev to Product Development. The new name of the rule must be unique in the entitlement policy.