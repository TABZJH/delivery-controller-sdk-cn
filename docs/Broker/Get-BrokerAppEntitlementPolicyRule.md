# Get-BrokerAppEntitlementPolicyRule

Gets application rules from the site's entitlement policy.

## 语法

    Get-BrokerAppEntitlementPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerAppEntitlementPolicyRule [[-Name] <String>] [-Description <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-LeasingBehavior <LeasingBehavior>] [-SessionReconnection <SessionReconnection>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns application rules matching the specified search criteria from the site's entitlement policy. If no search criteria are specified, all application rules in the entitlement policy are obtained.

An application rule in the entitlement policy defines the users who are allowed per-session access to a machine to run one or more applications published from the rule's desktop group.

\---\---\---\---\---\---\---\----- BrokerAppEntitlementPolicyRule Object The BrokerAppEntitlementPolicyRule object represents a single application rule within the site's entitlement policy. 其中包含以下属性：

    -- Description (System.String)
       Optional description of the rule. The text is purely informational for the administrator, it is never visible to the end user.
    
    -- DesktopGroupUid (System.Int32)
       The unique ID of the desktop group to which the rule applies.
    
    -- Enabled (System.Boolean)
       Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's entitlement policy.
    
    -- ExcludedUserFilterEnabled (System.Boolean)
       Indicates whether the excluded users filter of the rule is enabled. If the filter is disabled then any user entries in the filter are ignored when entitlement policy rules are evaluated.
    
    -- ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       The excluded users filter of the rule, that is, the users and groups who are explicitly denied entitlements to use published applications from the associated desktop group.
    
    -- IncludedUserFilterEnabled (System.Boolean)
       Indicates whether the included users filter of the rule is enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to an application session by the rule.
    
    -- IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       The included users filter of the rule, that is, the users and groups who are granted an entitlement to an application session by the rule.
    
       If a user appears explicitly in the excluded users filter of the rule or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter.
    
    -- LeasingBehavior (Citrix.Broker.Admin.SDK.LeasingBehavior)
       Defines the desired connection leasing behavior applied to sessions launched using this entitlement. Possible values are:
       Allowed and Disallowed.
    
    -- Name (System.String)
       The administrative name of the rule. Each rule in the site's entitlement policy must have a unique name (irrespective of whether they are desktop or application rules).
    
    -- SessionReconnection (Citrix.Broker.Admin.SDK.SessionReconnection)
       Defines reconnection (roaming) behavior for sessions launched using this rule. Possible values are:
       Always, DisconnectedOnly, and SameEndpointOnly.
    
    -- Uid (System.Int32)
       The unique ID of the rule itself.
    

## 相关命令

- [New-BrokerAppEntitlementPolicyRule](New-BrokerAppEntitlementPolicyRule.html)
- [Set-BrokerAppEntitlementPolicyRule](Set-BrokerAppEntitlementPolicyRule.html)
- [Rename-BrokerAppEntitlementPolicyRule](Rename-BrokerAppEntitlementPolicyRule.html)
- [Remove-BrokerAppEntitlementPolicyRule](Remove-BrokerAppEntitlementPolicyRule.html)

## 参数

| 名称                        | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                       | Gets the application rule with the specified unique ID.                                                                                                                          | true  | false |                                                                                        |
| 名称                        | Gets only application rules with the specified name.                                                                                                                             | false | false |                                                                                        |
| 说明                        | Gets only application rules with the specified description.                                                                                                                      | false | false |                                                                                        |
| DesktopGroupUid           | Gets only the application rule that applies to the desktop group with the specified unique ID.                                                                                   | false | false |                                                                                        |
| 已启用                       | Gets only application rules that are in the specified state, either enabled ($true), or disabled ($false).                                                                       | false | false |                                                                                        |
| ExcludedUser              | Gets only application rules that have the specified user in their excluded users filter (whether the filter is enabled or not).                                                  | false | false |                                                                                        |
| ExcludedUserFilterEnabled | Gets only application rules that have their excluded user filter enabled ($true) or disabled ($false).                                                                           | false | false |                                                                                        |
| IncludedUser              | Gets only application rules that have the specified user in their included users filter (whether the filter is enabled or not).                                                  | false | false |                                                                                        |
| IncludedUserFilterEnabled | Gets only application rules that have their included user filter enabled ($true) or disabled ($false).                                                                           | false | false |                                                                                        |
| LeasingBehavior           | Gets only application rules with the specified connection leasing behavior. Possible values are:  
Allowed and Disallowed.                                                       | false | false |                                                                                        |
| SessionReconnection       | Gets only application rules with the specified session reconnection behavior. Possible values are:  
Always, DisconnectedOnly, and SameEndpointOnly.                             | false | false |                                                                                        |
| ReturnTotalRecordCount    | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount            | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                        | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                    | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                       | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                        | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress              | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.AppEntitlementPolicyRule

Get-BrokerAppEntitlementPolicyRule returns all application rules from the entitlement policy that match the specified selection criteria.

## 示例

### 示例 1

    C:\PS> Get-BrokerAppEntitlementPolicyRule
    

Description  
\---\---\-----  
Returns all application rules from the entitlement policy. This offers a complete description of the current site's entitlement policy with respect to application entitlements from shared desktop groups.

### 示例 2

    C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'
    C:\PS> Get-BrokerAppEntitlementPolicyRule -DesktopGroupUid $dg.Uid
    

Description  
\---\---\-----  
Returns the application rule in the entitlement policy that grants users an entitlement to application sessions in the Customer Support desktop group.