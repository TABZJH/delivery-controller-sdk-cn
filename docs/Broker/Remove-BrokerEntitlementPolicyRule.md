# Remove-BrokerEntitlementPolicyRule

Deletes a desktop rule from the site's entitlement policy.

## 语法

    Remove-BrokerEntitlementPolicyRule [-InputObject] <EntitlementPolicyRule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerEntitlementPolicyRule [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerEntitlementPolicyRule cmdlet deletes a desktop rule from the site's entitlement policy.

A desktop rule in the entitlement policy defines the users who are allowed per-session access to a machine from the rule's associated desktop group to run a full desktop session.

Deleting a rule does not affect existing sessions launched using the rule, but users cannot reconnect to those sessions if they are subsequently disconnected.

## 相关命令

- [New-BrokerEntitlementPolicyRule](New-BrokerEntitlementPolicyRule.html)
- [Get-BrokerEntitlementPolicyRule](Get-BrokerEntitlementPolicyRule.html)
- [Set-BrokerEntitlementPolicyRule](Set-BrokerEntitlementPolicyRule.html)
- [Rename-BrokerEntitlementPolicyRule](Rename-BrokerEntitlementPolicyRule.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The desktop rule to be deleted from the entitlement policy.                                                                                                                     | true  | true (ByValue)        |                                                                                        |
| 名称           | The name of the desktop rule to be deleted from the entitlement policy.                                                                                                         | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.EntitlementPolicyRule

The desktop rule to be deleted from the entitlement policy.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerEntitlementPolicyRule 'Temp Workers'
    

Description  
\---\---\-----  
Deletes the desktop rule called Temp Workers from the entitlement policy. Existing desktop sessions launched using the rule are not affected, but users cannot reconnect to sessions if they are subsequently disconnected.

### 示例 2

    C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'
    C:\PS> Get-BrokerEntitlementPolicyRule -DesktopGroupUid $dg.Uid | Remove-BrokerEntitlementPolicyRule
    

Description  
\---\---\-----  
Deletes all desktop rules from the entitlement policy applying to the Customer Support desktop group. This effectively removes all access to the desktops published from this group. Existing desktop sessions are not affected, but users cannot reconnect to sessions if they are subsequently disconnected.