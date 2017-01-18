# Get-BrokerEntitlementPolicyRule

Gets desktop rules from the site's entitlement policy.

## 语法

    Get-BrokerEntitlementPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerEntitlementPolicyRule [[-Name] <String>] [-BrowserName <String>] [-ColorDepth <ColorDepth>] [-Description <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IconUid <Int32>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-LeasingBehavior <LeasingBehavior>] [-Metadata <String>] [-PublishedName <String>] [-RestrictToTag <String>] [-SecureIcaRequired <Boolean>] [-SessionReconnection <SessionReconnection>] [-UUID <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns desktop rules matching the specified search criteria from the site's entitlement policy. If no search criteria are specified, all desktop rules in the entitlement policy are obtained.

A desktop rule in the entitlement policy defines the users who are allowed per-session access to a machine from the rule's associated desktop group to run a full desktop session.

\---\---\---\---\---\---\---\----- BrokerEntitlementPolicyRule Object The BrokerEntitlementPolicyRule object represents a single desktop rule within the site's entitlement policy. 其中包含以下属性：

    -- BrowserName (System.String)
       Site-wide unique name identifying this desktop entitlement to other components (for example StoreFront).
    
    -- ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth?)
       The color depth of any desktop session launched by the user from the entitlement. If null, the equivalent setting from the rule's desktop group is used.
    
    -- Description (System.String)
       Optional description of the rule. The text may be visible to the end user, for example, as a tooltip associated with the desktop entitlement.
    
    -- DesktopGroupUid (System.Int32)
       The unique ID of the desktop group to which the rule applies.
    
    -- Enabled (System.Boolean)
       Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's entitlement policy.
    
    -- ExcludedUserFilterEnabled (System.Boolean)
       Indicates whether the excluded users filter is enabled. If the filter is disabled then any user entries in the filter are ignored when entitlement policy rules are evaluated.
    
    -- ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       The excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a desktop session from this rule.
    
    -- IconUid (System.Int32?)
       The unique ID of the icon used to display the desktop entitlement to the user. If null, the equivalent setting from the rule's desktop group is used.
    
    -- IncludedUserFilterEnabled (System.Boolean)
       Indicates whether the included users filter is enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to a desktop session by the rule.
    
    -- IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       The included users filter of the rule, that is, the users and groups who are granted an entitlement to a desktop session by the rule.
    
    -- LeasingBehavior (Citrix.Broker.Admin.SDK.LeasingBehavior)
       Defines the desired connection leasing behavior applied to sessions launched using this entitlement. Possible values are:
       Allowed and Disallowed.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       A collection of arbitrary key/value pairs that can be associated with the rule. The administrator can use these values for any purpose; they are not used by the site itself in any way.
    
    -- Name (System.String)
       The administrative name of the rule. Each rule in the site's entitlement policy must have a unique name (irrespective of whether they are desktop or application rules).
    
    -- PublishedName (System.String)
       The name of the desktop session entitlement as seen by the user. If null, the equivalent setting from the rule's desktop group is used.
    
    -- RestrictToTag (System.String)
       Optional tag that may be used further to restrict which machines may be made accessible to a user by an entitlement policy rule. A machine may be made accessible by an entitlement policy rule only if either the rule has no tag restriction or the rule does have a tag restriction and the machine is tagged with the same tag.
    
    -- SecureIcaRequired (System.Boolean?)
       Indicates whether the rule requires the SecureICA protocol for desktop sessions launched using the entitlement. If null, the equivalent setting from the rule's desktop group is used.
    
    -- SessionReconnection (Citrix.Broker.Admin.SDK.SessionReconnection)
       Defines reconnection (roaming) behavior for sessions launched using this rule. Possible values are:
       Always, DisconnectedOnly, and SameEndpointOnly.
    
    -- Uid (System.Int32)
       The unique ID of the rule itself.
    
    -- UUID (System.Guid)
       UUID of the rule.
    

## 相关命令

- [New-BrokerEntitlementPolicyRule](New-BrokerEntitlementPolicyRule.html)
- [Set-BrokerEntitlementPolicyRule](Set-BrokerEntitlementPolicyRule.html)
- [Rename-BrokerEntitlementPolicyRule](Rename-BrokerEntitlementPolicyRule.html)
- [Remove-BrokerEntitlementPolicyRule](Remove-BrokerEntitlementPolicyRule.html)

## 参数

| 名称                        | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                       | Gets the desktop rule with the specified unique ID.                                                                                                                              | true  | false |                                                                                        |
| 名称                        | Gets only desktop rules with the specified name.                                                                                                                                 | false | false |                                                                                        |
| BrowserName               | Gets only desktop rules with browser names matching the specified name.                                                                                                          | false | false |                                                                                        |
| ColorDepth                | Gets only desktop rules with the specified color depth.  
Valid values are $null, FourBit, EightBit, SixteenBit, and TwentyFourBit.                                              | false | false |                                                                                        |
| 说明                        | Gets only desktop rules with the specified description.                                                                                                                          | false | false |                                                                                        |
| DesktopGroupUid           | Gets only desktop rules that apply to the desktop group with the specified unique ID.                                                                                            | false | false |                                                                                        |
| 已启用                       | Gets only desktop rules that are in the specified state, either enabled ($true), or disabled ($false).                                                                           | false | false |                                                                                        |
| ExcludedUser              | Gets only desktop rules that have the specified user in their excluded users filter (whether the filter is enabled or not).                                                      | false | false |                                                                                        |
| ExcludedUserFilterEnabled | Gets only desktop rules that have their excluded user filter enabled ($true) or disabled ($false).                                                                               | false | false |                                                                                        |
| IconUid                   | Gets only desktop rules using the icon with the specified unique ID.                                                                                                             | false | false |                                                                                        |
| IncludedUser              | Gets only desktop rules that have the specified user in their included users filter (whether the filter is enabled or not).                                                      | false | false |                                                                                        |
| IncludedUserFilterEnabled | Gets only desktop rules that have their included user filter enabled ($true) or disabled ($false).                                                                               | false | false |                                                                                        |
| LeasingBehavior           | Gets only application rules with the specified connection leasing behavior. Possible values are:  
Allowed and Disallowed.                                                       | false | false |                                                                                        |
| 元数据                       | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                        | false | false |                                                                                        |
| PublishedName             | Gets only desktop rules with the specified published name, that is, the desktop session entitlement name that the end user sees.                                                 | false | false |                                                                                        |
| RestrictToTag             | Gets only desktop rules with the specified tag restriction.                                                                                                                      | false | false |                                                                                        |
| SecureIcaRequired         | Gets only desktop rules that require the desktop session to use the SecureICA protocol ($true) or not ($false).                                                                  | false | false |                                                                                        |
| SessionReconnection       | Gets only desktop rules with the specified session reconnection behavior. Possible values are:  
Always, DisconnectedOnly, and SameEndpointOnly.                                 | false | false |                                                                                        |
| UUID                      | Gets rules with the specified value of UUID.                                                                                                                                     | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.EntitlementPolicyRule

Get-BrokerEntitlementPolicyRule returns all desktop entitlement policy rules that match the specified selection criteria.

## 示例

### 示例 1

    C:\PS> Get-BrokerEntitlementPolicyRule
    

Description  
\---\---\-----  
Returns all desktop rules from the entitlement policy. This offers a complete description of the current site's entitlement policy with respect to desktops published from shared desktop groups.

### 示例 2

    C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'
    C:\PS> Get-BrokerEntitlementPolicyRule -DesktopGroupUid $dg.Uid
    

Description  
\---\---\-----  
Returns all desktop rules in the entitlement policy that give users entitlements to desktop sessions in the Customer Support desktop group.