# Get-BrokerAccessPolicyRule

Gets rules from the site's access policy.

## 语法

    Get-BrokerAccessPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerAccessPolicyRule [[-Name] <String>] [-AllowedConnections <AllowedConnection>] [-AllowedUsers <AllowedUser>] [-Description <String>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedClientIPFilterEnabled <Boolean>] [-ExcludedClientName <String>] [-ExcludedClientNameFilterEnabled <Boolean>] [-ExcludedSmartAccessFilterEnabled <Boolean>] [-ExcludedSmartAccessTag <String>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IncludedClientIPFilterEnabled <Boolean>] [-IncludedClientName <String>] [-IncludedClientNameFilterEnabled <Boolean>] [-IncludedSmartAccessFilterEnabled <Boolean>] [-IncludedSmartAccessTag <String>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-Metadata <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns rules matching the specified search criteria from the site's access policy. If no search criteria are specified, all rules in the access policy are obtained.

An access policy rule defines a set of connection filters and access control rights relating to a desktop group. These allow fine-grained control of what access is granted to a desktop group based on details of, for example, a user's endpoint device, its address, and the user's identity.

\---\---\---\---\---\---\---\----- BrokerAccessPolicyRule Object A BrokerAccessPolicyRule object represents a single rule within the site's access policy. For a user to gain access to a desktop group via the rule their connection must match all its enabled include filters, and none of its enabled exclude filters. The object contains the following properties:

    -- AllowedConnections (Citrix.Broker.Admin.SDK.AllowedConnection)
       Controls whether connections must be local or via Access Gateway, and if so whether specified SmartAccess tags must be provided by Access Gateway with the connection. This property forms part of the included SmartAccess tags filter.
    
       For a detailed description of this property see "help about_Broker_AccessPolicy".
    
    -- AllowedProtocols (System.String[])
       Protocols (for example HDX, RDP) available to the user for sessions delivered from the rule's desktop group. If the user gains access to a desktop group by multiple rules, the allowed protocol list is the combination of the protocol lists from all those rules.
    
       If the protocol list is empty, access to the desktop group is implicitly denied.
    
    -- AllowedUsers (Citrix.Broker.Admin.SDK.AllowedUser)
       Controls the behavior of the included users filter. This can restrict access to a list of named users or groups, or allow access to any authenticated user. For a detailed description of this property see "help about_Broker_AccessPolicy".
    
    -- AllowRestart (System.Boolean)
       Indicates if the user can restart sessions delivered from the rule's desktop group. Session restart is handled as follows: For sessions on single-session power-managed machines, the machine is powered off, and a new session launch request made; for sessions on multi-session machines, a logoff request is issued to the session, and a new session launch request made; otherwise the property is ignored.
    
    -- Description (System.String)
       An optional description of the rule. The text is purely informational for the administrator, it is never visible to the end user.
    
    -- DesktopGroupName (System.String)
       The name of the desktop group to which the rule applies.
    
    -- DesktopGroupUid (System.Int32)
       The unique ID of the desktop group to which the rule applies.
    
    -- Enabled (System.Boolean)
       Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's access policy.
    
    -- ExcludedClientIPFilterEnabled (System.Boolean)
       Indicates whether the excluded client IP filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.
    
    -- ExcludedClientIPs (Citrix.Broker.Admin.SDK.ChbIPAddressRange[])
       IP addresses of user devices explicitly denied access to the rule's desktop group. Addresses can be specified as simple numeric addresses or as subnet masks (for example, 10.40.37.5 or 10.40.0.0/16). This property forms part of the excluded client IP address filter.
    
    -- ExcludedClientNameFilterEnabled (System.Boolean)
       Indicates whether the excluded client name filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.
    
    -- ExcludedClientNames (System.String[])
       Names of user devices explicitly denied access to the rule's desktop group. This property forms part of the excluded client names filter.
    
    -- ExcludedSmartAccessFilterEnabled (System.Boolean)
       Indicates whether the excluded SmartAccess tags filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.
    
    -- ExcludedSmartAccessTags (System.String[])
       SmartAccess tags which explicitly deny access to the rule's desktop group if any occur in those provided by Access Gateway with the user's connection. This property forms part of the excluded SmartAccess tags filter.
    
    -- ExcludedUserFilterEnabled (System.Boolean)
       Indicates whether the excluded users filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.
    
    -- ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       Users and groups who are explicitly denied access to the rule's desktop group. This property forms part of the excluded users filter.
    
    -- HdxSslEnabled (System.Boolean)
       Indicates whether TLS encryption is enabled for sessions delivered from the rule's desktop group.
    
    -- IncludedClientIPFilterEnabled (System.Boolean)
       Indicates whether the included client IP filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.
    
    -- IncludedClientIPs (Citrix.Broker.Admin.SDK.ChbIPAddressRange[])
       IP addresses of user devices allowed access to the rule's desktop group. Addresses can be specified as simple numeric addresses or as subnet masks (for example, 10.40.37.5 or 10.40.0.0/16). This property forms part of the included client IP address filter.
    
    -- IncludedClientNameFilterEnabled (System.Boolean)
       Indicates whether the included client names filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.
    
    -- IncludedClientNames (System.String[])
       Names of user devices allowed access to the rule's desktop group. This property forms part of the included client names filter.
    
    -- IncludedSmartAccessFilterEnabled (System.Boolean)
       Indicates whether the included SmartAccess tags filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.
    
    -- IncludedSmartAccessTags (System.String[])
       The SmartAccess tags which grant access to the rule's desktop group if any occur in those provided by Access Gateway with the user's connection. This property forms part of the excluded SmartAccess tags filter.
    
    -- IncludedUserFilterEnabled (System.Boolean)
       Indicates whether the included users filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.
    
    -- IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser[])
       Users and groups who are granted access to the rule's desktop group. This property forms part of the included users filter.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       A collection of arbitrary key/value pairs that can be associated with the rule. The administrator can use these values for any purpose; they are not used by the site itself in any way.
    
    -- Name (System.String)
       Administrative name of the rule. Each rule in the site's access policy must have a unique name.
    
    -- Uid (System.Int32)
       Unique ID of the rule itself.
    

## 相关命令

- [New-BrokerAccessPolicyRule](New-BrokerAccessPolicyRule.html)
- [Set-BrokerAccessPolicyRule](Set-BrokerAccessPolicyRule.html)
- [Rename-BrokerAccessPolicyRule](Rename-BrokerAccessPolicyRule.html)
- [Remove-BrokerAccessPolicyRule](Remove-BrokerAccessPolicyRule.html)

## 参数

| 名称                               | 说明                                                                                                                                                                                                    | 是否必需？ | 管道输入  | 默认值                                                                                    |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                              | Gets only the rule with the specified unique ID.                                                                                                                                                      | true  | false |                                                                                        |
| 名称                               | Gets only rules with the specified name.                                                                                                                                                              | false | false |                                                                                        |
| AllowedConnections               | Gets only rules that have the specified value in the AllowedConnections property of their included SmartAccess tags filter.  
Valid values are Filtered, NotViaAG, ViaAG and AnyViaAG.                | false | false |                                                                                        |
| AllowedUsers                     | Gets only rules that have the specified value in the AllowedUsers property of their included users filter.  
Valid values are Filtered, AnyAuthenticated, Any, AnonymousOnly and FilteredOrAnonymous. | false | false |                                                                                        |
| 说明                               | Gets only rules with the specified description.                                                                                                                                                       | false | false |                                                                                        |
| DesktopGroupName                 | Gets only rules applying to desktop groups with names matching the specified name.                                                                                                                    | false | false |                                                                                        |
| DesktopGroupUid                  | Gets only rules that apply to the desktop group with the specified unique ID.                                                                                                                         | false | false |                                                                                        |
| 已启用                              | Gets only rules that are in the specified state, either enabled ($true) or disabled ($false).                                                                                                         | false | false |                                                                                        |
| ExcludedClientIPFilterEnabled    | Gets only rules that have their excluded client IP address filter enabled ($true) or disabled ($false).                                                                                               | false | false |                                                                                        |
| ExcludedClientName               | Gets only rules that have the specified client name in their excluded client names filter (whether the filter is enabled or not).                                                                     | false | false |                                                                                        |
| ExcludedClientNameFilterEnabled  | Gets only rules that have their excluded client name filter enabled ($true) or disabled ($false).                                                                                                     | false | false |                                                                                        |
| ExcludedSmartAccessFilterEnabled | Gets only rules that have their excluded SmartAccess tags filter enabled ($true) or disabled ($false).                                                                                                | false | false |                                                                                        |
| ExcludedSmartAccessTag           | Gets only rules that have the specified SmartAccess tag in their excluded SmartAccess tags filter (whether the filter is enabled or not).                                                             | false | false |                                                                                        |
| ExcludedUser                     | Gets only rules that have the specified user in their excluded users filter (whether the filter is enabled or not).                                                                                   | false | false |                                                                                        |
| ExcludedUserFilterEnabled        | Gets only rules that have their excluded user filter enabled ($true) or disabled ($false).                                                                                                            | false | false |                                                                                        |
| IncludedClientIPFilterEnabled    | Gets only rules that have their included client IP address filter enabled ($true) or disabled ($false).                                                                                               | false | false |                                                                                        |
| IncludedClientName               | Gets only rules that have the specified user device name in their included client names filter (whether the filter is enabled or not).                                                                | false | false |                                                                                        |
| IncludedClientNameFilterEnabled  | Gets only rules that have their included client name filter enabled ($true) or disabled ($false).                                                                                                     | false | false |                                                                                        |
| IncludedSmartAccessFilterEnabled | Gets only rules that have their included SmartAccess tags filter enabled ($true) or disabled ($false).                                                                                                | false | false |                                                                                        |
| IncludedSmartAccessTag           | Gets only rules that have the specified SmartAccess tag in their included SmartAccess tags filter (whether the filter is enabled or not).                                                             | false | false |                                                                                        |
| IncludedUser                     | Gets only rules that have the specified user in their included users filter (whether the filter is enabled or not).                                                                                   | false | false |                                                                                        |
| IncludedUserFilterEnabled        | Gets only rules that have their included user filter enabled ($true) or disabled ($false).                                                                                                            | false | false |                                                                                        |
| 元数据                              | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                                             | false | false |                                                                                        |
| ReturnTotalRecordCount           | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                      | false | false | False                                                                                  |
| MaxRecordCount                   | 指定要返回的最大记录数。                                                                                                                                                                                          | false | false | 250                                                                                    |
| 跳过                               | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                 | false | false |                                                                                        |
| SortBy                           | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                              | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                              | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                               | false | false |                                                                                        |
| 属性                               | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                | false | false |                                                                                        |
| AdminAddress                     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                    | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.AccessPolicyRule

Get-BrokerAccessPolicyRule returns all access policy rules that match the specified selection criteria.

## 示例

### 示例 1

    C:\PS> Get-BrokerAccessPolicyRule
    

Description  
\---\---\-----  
Returns all access policy rules. This offers a complete description of the current site's access policy.

### 示例 2

    C:\PS> Get-BrokerAccessPolicyRule -Enabled $true -IncludedUser sales\tech-support
    

Description  
\---\---\-----  
Returns all rules that are both enabled and explicitly include the SALES\tech-support group in their included users filter.