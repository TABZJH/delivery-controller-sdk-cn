# Remove-BrokerAppEntitlementPolicyRule

Deletes an application rule from the site's entitlement policy.

## 语法

    Remove-BrokerAppEntitlementPolicyRule [-InputObject] <AppEntitlementPolicyRule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerAppEntitlementPolicyRule [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerAppEntitlementPolicyRule cmdlet deletes an application rule from the site's entitlement policy.

An application rule in the entitlement policy defines the users who are allowed per-session access to a machine to run one or more applications published from the rule's desktop group.

Deleting a rule does not affect existing sessions launched using the rule, but users cannot reconnect to those sessions if they are subsequently disconnected.

## 相关命令

- [New-BrokerAppEntitlementPolicyRule](New-BrokerAppEntitlementPolicyRule.html)
- [Get-BrokerAppEntitlementPolicyRule](Get-BrokerAppEntitlementPolicyRule.html)
- [Set-BrokerAppEntitlementPolicyRule](Set-BrokerAppEntitlementPolicyRule.html)
- [Rename-BrokerAppEntitlementPolicyRule](Rename-BrokerAppEntitlementPolicyRule.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The application rule to be deleted from the entitlement policy.                                                                                                                 | true  | true (ByValue)        |                                                                                        |
| 名称           | The name of the application rule to be deleted from the entitlement policy.                                                                                                     | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.AppEntitlementPolicyRule

The application rule to be deleted from the entitlement policy.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerAppEntitlementPolicyRule 'Temp Workers'
    

Description  
\---\---\-----  
Deletes the application rule called Temp Workers from the entitlement policy rule. Existing application sessions launched using that rule are not affected, but users cannot reconnect to those sessions if they are subsequently disconnected.

### 示例 2

    C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'
    C:\PS> Get-BrokerAppEntitlementPolicyRule -DesktopGroupUid $dg.Uid | Remove-BrokerAppEntitlementPolicyRule
    

Description  
\---\---\-----  
Deletes the application rule from the entitlement policy rule applied to the Customer Support desktop group. This effectively removes all access to the applications published from this group. Existing application sessions are not affected, but users cannot reconnect to those sessions if they are subsequently disconnected.