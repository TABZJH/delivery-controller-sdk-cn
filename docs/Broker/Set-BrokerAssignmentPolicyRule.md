# Set-BrokerAssignmentPolicyRule

Modifies an existing desktop rule in the site's assignment policy.

## 语法

    Set-BrokerAssignmentPolicyRule [-InputObject] <AssignmentPolicyRule[]> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-ColorDepth <ColorDepth>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IconUid <Int32>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-MaxDesktops <Int32>] [-PublishedName <String>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-SecureIcaRequired <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerAssignmentPolicyRule [-Name] <String> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-ColorDepth <ColorDepth>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IconUid <Int32>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-MaxDesktops <Int32>] [-PublishedName <String>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-SecureIcaRequired <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerAssignmentPolicyRule cmdlet modifies an existing desktop rule in the site's assignment policy.

A desktop rule in the assignment policy defines the users who are entitled to self-service persistent machine assignments from the rule's desktop group. A rule defines how many machines a user is allowed from the group for delivery of full desktop sessions.

Changing a desktop rule does not alter machine assignments that have already been made by the rule, nor does it affect active sessions to those machines in any way.

## 相关命令

- [New-BrokerAssignmentPolicyRule](New-BrokerAssignmentPolicyRule.html)
- [Get-BrokerAssignmentPolicyRule](Get-BrokerAssignmentPolicyRule.html)
- [Rename-BrokerAssignmentPolicyRule](Rename-BrokerAssignmentPolicyRule.html)
- [Remove-BrokerAssignmentPolicyRule](Remove-BrokerAssignmentPolicyRule.html)

## 参数

| 名称                        | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject               | The desktop rule in the assignment policy to be modified.                                                                                                                                                                                                                                                                                                                                                                                                                                                     | true  | true (ByValue)        |                                                                                        |
| 名称                        | Specifies the name of the desktop rule in the assignment policy to be modified.                                                                                                                                                                                                                                                                                                                                                                                                                               | true  | true (ByPropertyName) |                                                                                        |
| PassThru                  | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                                                                                                                                                                                                                                                                                                                | false | false                 | False                                                                                  |
| AddExcludedUsers          | Adds the specified users to the excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from this rule.  
See the ExcludedUsers parameter for more information.                                                                                                                                                                                                                                                                     | false | false                 |                                                                                        |
| AddIncludedUsers          | Adds the specified users to the included users filter of the rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.  
See the IncludedUsers parameter for more information.                                                                                                                                                                                                                                                                                  | false | false                 |                                                                                        |
| ColorDepth                | Changes the color depth of any desktop sessions to machines assigned by the rule.  
Valid values are $null, FourBit, EightBit, SixteenBit, and TwentyFourBit.  
The default null value indicates that the equivalent setting from the rule's desktop group is used.                                                                                                                                                                                                                                           | false | false                 |                                                                                        |
| 说明                        | Changes the description of the desktop rule. The text may be visible to the end user, for example, as a tooltip associated with the desktop entitlement.  
A null value indicates that the equivalent setting from the rule's desktop group is used.                                                                                                                                                                                                                                                          | false | false                 |                                                                                        |
| 已启用                       | Enables or disables the desktop rule. A disabled rule is ignored when evaluating the site's assignment policy.                                                                                                                                                                                                                                                                                                                                                                                                | false | false                 |                                                                                        |
| ExcludedUserFilterEnabled | Enables or disables the excluded users filter. If the filter is disabled then any user entries in the filter are ignored when assignment policy rules are evaluated.                                                                                                                                                                                                                                                                                                                                          | false | false                 |                                                                                        |
| ExcludedUsers             | Changes the excluded users filter of the desktop rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from this rule.  
This can be used to exclude users or groups who would otherwise gain access by groups specified in the included users filter.                                                                                                                                                                                                         | false | false                 |                                                                                        |
| IconUid                   | Changes the unique ID of the icon used to display the machine assignment entitlement to the user, and of the assigned desktop itself following the assignment.  
The default null value indicates that the equivalent setting from the rule's desktop group is used.                                                                                                                                                                                                                                          | false | false                 |                                                                                        |
| IncludedUserFilterEnabled | Enables or disables the included users filter. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to a machine assignment by the rule.  
Users who would be implicitly granted access when the filter is disabled can still be explicitly denied access using the excluded users filter.  
For rules that relate to RemotePC desktop groups however, if the included user filter is disabled, the rule is effectively disabled. | false | false                 |                                                                                        |
| IncludedUsers             | Changes the included users filter of the rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.  
If a user appears explicitly in the excluded users filter of the rule, or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter.                                                                                                                        | false | false                 |                                                                                        |
| MaxDesktops               | The number of machines from the rule's desktop group to which a user is entitled. Where an entitlement is granted to a user group rather than an individual, the number of machines applies to each member of the user group independently.                                                                                                                                                                                                                                                                   | false | false                 |                                                                                        |
| PublishedName             | Changes the published name of the machine assignment entitlement as seen by the user. Changing the published name does not affect the names of desktops that have already been assigned by the rule.  
The default null value indicates that the equivalent setting from the rule's desktop group is used.                                                                                                                                                                                                    | false | false                 |                                                                                        |
| RemoveExcludedUsers       | Removes the specified users from the excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from this rule.  
See the ExcludedUsers parameter for more information.                                                                                                                                                                                                                                                                | false | false                 |                                                                                        |
| RemoveIncludedUsers       | Removes the specified users from the included users filter of the desktop rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.  
See the IncludedUsers parameter for more information.                                                                                                                                                                                                                                                                     | false | false                 |                                                                                        |
| SecureIcaRequired         | Changes whether the desktop rule requires the SecureICA protocol for desktop sessions to machines assigned using the entitlement.  
The default null value indicates that the equivalent setting from the rule's desktop group is used.                                                                                                                                                                                                                                                                       | false | false                 |                                                                                        |
| LoggingId                 | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                                               | false | false                 |                                                                                        |
| AdminAddress              | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                                                                                            | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.AssignmentPolicyRule

The desktop rule within the assignment policy to be modified.

## 返回值

### None or Citrix.Broker.Admin.SDK.AssignmentPolicyRule

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AssignmentPolicyRule object.

## 示例

### 示例 1

    C:\PS> Set-BrokerAssignmentPolicyRule 'Temp Staff' -AddIncludedUsers office\interns
    

Description  
\---\---\-----  
Adds the user group OFFICE\interns to the Temp Staff desktop rule in the assignment policy. This grants all members of that user group entitlements to machines in the rule's desktop group. The number of machine entitlements per user and the session properties of the desktops obtained using the rule are determined by the rule's other properties.

### 示例 2

    C:\PS> Set-BrokerAssignmentPolicyRule 'Temp Staff' -Enabled $false
    

Description  
\---\---\-----  
Disables the Temp Staff desktop rule in the assignment policy. This prevents further machine assignments being made using this rule until it is re-enabled. However, access to machines already assigned using the rule is not impacted.