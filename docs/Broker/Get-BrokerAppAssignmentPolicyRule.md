# Get-BrokerAppAssignmentPolicyRule

Gets application rules from the site's assignment policy.

## 语法

    Get-BrokerAppAssignmentPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerAppAssignmentPolicyRule [[-Name] <String>] [-Description <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns application rules matching the specified search criteria from the site's assignment policy. If no search criteria are specified, all application rules in the assignment policy are obtained.

An application rule in the assignment policy defines the users who are entitled to a self-service persistent machine assignment from the rule's desktop group; once assigned the machine can run one or more applications published from the group.

\---\---\---\---\---\---\---\----- BrokerAppAssignmentPolicyRule Object The BrokerAppAssignmentPolicyRule object represents a single application rule within the site's assignment policy. 其中包含以下属性：

    -- Description (System.String)
       An optional description of the rule. The text is purely informational for the administrator, it is never visible to the end user.
    
    -- DesktopGroupUid (System.Int32)
       The unique ID of the desktop group to which the rule applies.
    
    -- Enabled (System.Boolean)
       Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's assignment policy.
    
    -- ExcludedUserFilterEnabled (System.Boolean)
       Indicates whether the excluded users filter is enabled. If the filter is disabled then any user entries in the filter are ignored when assignment policy rules are evaluated.
    
    -- ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       The excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from the rule's desktop group.
    
    -- IncludedUserFilterEnabled (System.Boolean)
       Indicates whether the included users filter is enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly entitled to the machine assignment described by the rule.
    
    -- IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       The included users filter of the rule, that is, the users and groups who are entitled to a machine assignment from the rule's desktop group.
    
    -- Name (System.String)
       The administrative name of the rule. Each rule in the site's assignment policy must have a unique name (irrespective of whether they are desktop or application rules).
    
    -- Uid (System.Int32)
       The unique ID of the rule itself.
    

## 相关命令

- [New-BrokerAppAssignmentPolicyRule](New-BrokerAppAssignmentPolicyRule.html)
- [Set-BrokerAppAssignmentPolicyRule](Set-BrokerAppAssignmentPolicyRule.html)
- [Rename-BrokerAppAssignmentPolicyRule](Rename-BrokerAppAssignmentPolicyRule.html)
- [Remove-BrokerAppAssignmentPolicyRule](Remove-BrokerAppAssignmentPolicyRule.html)

## 参数

| 名称                        | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                       | Gets the application rule with the specified unique ID.                                                                                                                          | true  | false |                                                                                        |
| 名称                        | Gets only application rules with the specified name.                                                                                                                             | false | false |                                                                                        |
| 说明                        | Gets only application rules with the specified description.                                                                                                                      | false | false |                                                                                        |
| DesktopGroupUid           | Gets only application rules that apply to the desktop group with the specified unique ID.                                                                                        | false | false |                                                                                        |
| 已启用                       | Gets only application rules that are in the specified state, either enabled ($true) or disabled ($false).                                                                        | false | false |                                                                                        |
| ExcludedUser              | Gets only application rules that have the specified user in their excluded users filter (whether the filter is enabled or not)                                                   | false | false |                                                                                        |
| ExcludedUserFilterEnabled | Gets only application rules that have their excluded user filter enabled ($true) or disabled ($false).                                                                           | false | false |                                                                                        |
| IncludedUser              | Gets only application rules that have the specified user in their included users filter (whether the filter is enabled or not).                                                  | false | false |                                                                                        |
| IncludedUserFilterEnabled | Gets only application rules that have their included user filter enabled ($true) or disabled ($false).                                                                           | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.AppAssignmentPolicyRule

Get-BrokerAppAssignmentPolicyRule returns all application rules in the assignment policy that match the specified selection criteria.

## 示例

### 示例 1

    C:\PS> Get-BrokerAppAssignmentPolicyRule
    

Description  
\---\---\-----  
Returns all application rules from the assignment policy. This offers a complete description of the current site's assignment policy with respect to machine assignment entitlements for delivery of application sessions from private desktop groups.

### 示例 2

    C:\PS> $dg = Get-BrokerDesktopGroup 'Sales Support'
    C:\PS> Get-BrokerAppAssignmentPolicyRule -DesktopGroupUid $dg.Uid
    

Description  
\---\---\-----  
Returns the rule in the assignment policy that gives users entitlements to machine assignments in the Sales Support desktop group for delivery of application sessions.