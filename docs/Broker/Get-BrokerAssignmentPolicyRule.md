# Get-BrokerAssignmentPolicyRule

Gets desktop rules from the site's assignment policy.

## 语法

    Get-BrokerAssignmentPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerAssignmentPolicyRule [[-Name] <String>] [-ColorDepth <ColorDepth>] [-Description <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IconUid <Int32>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-MaxDesktops <Int32>] [-Metadata <String>] [-PublishedName <String>] [-SecureIcaRequired <Boolean>] [-UUID <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns desktop rules matching the specified search criteria from the site's assignment policy. If no search criteria are specified, all desktop rules in the assignment policy are obtained.

A desktop rule in the assignment policy defines the users who are entitled to self-service persistent machine assignments from the rule's desktop group. A rule defines how many machines a user is allowed from the group for delivery of full desktop sessions.

\---\---\---\---\---\---\---\----- BrokerAssignmentPolicyRule Object The BrokerAssignmentPolicyRule object represents a single desktop rule within the site's assignment policy. 其中包含以下属性：

    -- ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth?)
       The color depth of desktop sessions launched by the user from machines assigned to them by the rule. If null, the equivalent setting from the rule's desktop group is used.
    
    -- Description (System.String)
       Optional description of the rule. The text may be visible to the end user, for example, as a tooltip associated with the desktop entitlement.
    
    -- DesktopGroupUid (System.Int32)
       The unique ID of the desktop group to which the rule applies.
    
    -- Enabled (System.Boolean)
       Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's assignment policy.
    
    -- ExcludedUserFilterEnabled (System.Boolean)
       Indicates whether the excluded users filter is enabled. If the filter is disabled then any user entries in the filter are ignored when assignment policy rules are evaluated.
    
    -- ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       The excluded users filter of the rule, that is, the users and groups who are explicitly denied entitlements to machine assignments from the rule's desktop group.
    
    -- IconUid (System.Int32?)
       The unique ID of the icon used for the machine entitlement seen by the user or, after a machine is assigned by the rule, the icon for the desktop itself. If null, the equivalent setting from the rule's desktop group is used.
    
    -- IncludedUserFilterEnabled (System.Boolean)
       Indicates whether the included users filter is enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly entitled to the machine assignments described by the rule.
    
       For rules that relate to RemotePC desktop groups however, if the included user filter is disabled, the rule is effectively disabled.
    
    -- IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       The included users filter of the rule, that is, the users and groups who are entitled to machine assignments from the rule's desktop group.
    
    -- MaxDesktops (System.Int32)
       The number of machines from the rule's desktop group to which a user is entitled. Where an entitlement is granted to a user group rather than an individual, the number of machines applies to each member of the user group independently.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       A collection of arbitrary key/value pairs that can be associated with the rule. The administrator can use these values for any purpose; they are not used by the site itself in any way.
    
    -- Name (System.String)
       The administrative name of the rule. Each rule in the site's assignment policy must have a unique name (irrespective of whether they are desktop or application rules).
    
    -- PublishedName (System.String)
       The published name of the desktop entitlement seen by the user or, after a machine is assigned by the rule, the published name of the desktop itself. If null, the equivalent setting from the rule's desktop group is used.
    
    -- SecureIcaRequired (System.Boolean?)
       Indicates whether the rule requires the SecureICA protocol for desktop sessions launched using a machine assigned by the rule. If null, the equivalent setting from the rule's desktop group is used.
    
    -- Uid (System.Int32)
       The unique ID of the rule itself.
    
    -- UUID (System.Guid)
       UUID of the rule.
    

## 相关命令

- [New-BrokerAssignmentPolicyRule](New-BrokerAssignmentPolicyRule.html)
- [Set-BrokerAssignmentPolicyRule](Set-BrokerAssignmentPolicyRule.html)
- [Rename-BrokerAssignmentPolicyRule](Rename-BrokerAssignmentPolicyRule.html)
- [Remove-BrokerAssignmentPolicyRule](Remove-BrokerAssignmentPolicyRule.html)

## 参数

| 名称                        | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                       | Gets the desktop rule with the specified unique ID.                                                                                                                              | true  | false |                                                                                        |
| 名称                        | Gets only desktop rules with the specified name.                                                                                                                                 | false | false |                                                                                        |
| ColorDepth                | Gets only desktop rules with the specified color depth.  
Valid values are $null, FourBit, EightBit, SixteenBit, and TwentyFourBit.                                              | false | false |                                                                                        |
| 说明                        | Gets only desktop rules with the specified description.                                                                                                                          | false | false |                                                                                        |
| DesktopGroupUid           | Gets only desktop rules that apply to the desktop group with the specified unique ID.                                                                                            | false | false |                                                                                        |
| 已启用                       | Gets only rules that are in the specified state, either enabled ($true) or disabled ($false).                                                                                    | false | false |                                                                                        |
| ExcludedUser              | Gets only desktop rules that have the specified user in their excluded users filter (whether the filter is enabled or not).                                                      | false | false |                                                                                        |
| ExcludedUserFilterEnabled | Gets only desktop rules that have their excluded user filter enabled ($true) or disabled ($false).                                                                               | false | false |                                                                                        |
| IconUid                   | Gets only desktop rules using the icon with the specified unique ID.                                                                                                             | false | false |                                                                                        |
| IncludedUser              | Gets only desktop rules that have the specified user in their included users filter (whether the filter is enabled or not).                                                      | false | false |                                                                                        |
| IncludedUserFilterEnabled | Gets only desktop rules that have their included user filter enabled ($true) or disabled ($false).                                                                               | false | false |                                                                                        |
| MaxDesktops               | Gets only desktop rules granting the specified number of machine assignment entitlements.                                                                                        | false | false |                                                                                        |
| 元数据                       | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                        | false | false |                                                                                        |
| PublishedName             | Gets only desktop rules with the specified published name, that is, the desktop name that the end user sees.                                                                     | false | false |                                                                                        |
| SecureIcaRequired         | Gets only desktop rules that require desktop sessions to machines assigned by the rule to use the SecureICA protocol ($true) or not ($false).                                    | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.AssignmentPolicyRule

Get-BrokerAssignmentPolicyRule returns all assignment policy rules that match the specified selection criteria.

## 示例

### 示例 1

    C:\PS> Get-BrokerAssignmentPolicyRule
    

Description  
\---\---\-----  
Returns all desktop rules from the assignment policy. This offers a complete description of the current site's assignment policy with respect to machine assignment entitlements for delivery of desktop sessions from private desktop groups.

### 示例 2

    C:\PS> $dg = Get-BrokerDesktopGroup 'Sales Support'
    C:\PS> Get-BrokerAssignmentPolicyRule -DesktopGroupUid $dg.Uid
    

Description  
\---\---\-----  
Returns all rules in the assignment policy that give users entitlements to machine assignments in the Sales Support desktop group for delivery of full desktop sessions.