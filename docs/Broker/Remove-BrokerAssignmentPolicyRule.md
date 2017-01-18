# Remove-BrokerAssignmentPolicyRule

Deletes a desktop rule from the site's assignment policy.

## 语法

    Remove-BrokerAssignmentPolicyRule [-InputObject] <AssignmentPolicyRule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerAssignmentPolicyRule [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerAssignmentPolicyRule cmdlet deletes a desktop rule from the site's assignment policy.

A desktop rule in the assignment policy defines the users who are entitled to self-service persistent machine assignments from the rule's desktop group. A rule defines how many machines a user is allowed from the group for delivery of full desktop sessions.

Deleting a desktop rule does not remove machine assignments that have already been made by the rule, nor does it affect active sessions to those machines in any way.

## 相关命令

- [New-BrokerAssignmentPolicyRule](New-BrokerAssignmentPolicyRule.html)
- [Get-BrokerAssignmentPolicyRule](Get-BrokerAssignmentPolicyRule.html)
- [Set-BrokerAssignmentPolicyRule](Set-BrokerAssignmentPolicyRule.html)
- [Rename-BrokerAssignmentPolicyRule](Rename-BrokerAssignmentPolicyRule.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The desktop rule to be deleted from the assignment policy.                                                                                                                      | true  | true (ByValue)        |                                                                                        |
| 名称           | The name of the desktop rule to be deleted from the assignment policy.                                                                                                          | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.AssignmentPolicyRule

The desktop rule to be deleted from the assignment policy.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerAssignmentPolicyRule 'Temp Staff'
    

Description  
\---\---\-----  
Deletes the desktop rule called Temp Staff from the assignment policy. Access to machines already assigned by this rule is not affected in any way.

### 示例 2

    C:\PS> $dg = Get-BrokerDesktopGroup 'Sales Support'
    C:\PS> Get-BrokerAssignmentPolicyRule -DesktopGroupUid $dg.Uid | Remove-BrokerAssignmentPolicyRule
    

Description  
\---\---\-----  
Deletes all desktop rules for the Sales Support desktop group from the site's assignment policy. This prevents any further machine assignments being made from this group, but it does not affect existing assignments made by these rules.