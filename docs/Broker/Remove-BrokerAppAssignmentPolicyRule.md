# Remove-BrokerAppAssignmentPolicyRule

Deletes an application rule from the site's assignment policy.

## 语法

    Remove-BrokerAppAssignmentPolicyRule [-InputObject] <AppAssignmentPolicyRule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerAppAssignmentPolicyRule [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerAppAssignmentPolicyRule cmdlet deletes an application rule from the site's assignment policy.

An application rule in the assignment policy defines the users who are entitled to a self-service persistent machine assignment from the rule's desktop group; once assigned the machine can run one or more applications published from the group.

Deleting an application rule does not remove machine assignments that have already been made by the rule, nor does it affect active sessions to those machines in any way.

## 相关命令

- [New-BrokerAppAssignmentPolicyRule](New-BrokerAppAssignmentPolicyRule.html)
- [Get-BrokerAppAssignmentPolicyRule](Get-BrokerAppAssignmentPolicyRule.html)
- [Set-BrokerAppAssignmentPolicyRule](Set-BrokerAppAssignmentPolicyRule.html)
- [Rename-BrokerAppAssignmentPolicyRule](Rename-BrokerAppAssignmentPolicyRule.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The application rule to be deleted from the assignment policy.                                                                                                                  | true  | true (ByValue)        |                                                                                        |
| 名称           | The name of the application rule to be deleted from the assignment policy.                                                                                                      | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.AppAssignmentPolicyRule

The application rule to be deleted from the assignment policy.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerAppAssignmentPolicyRule 'Temp Staff'
    

Description  
\---\---\-----  
Deletes the application rule called Temp Staff from the assignment policy. Access to machines already assigned by this rule is not affected in any way.

### 示例 2

    C:\PS> $dg = Get-BrokerDesktopGroup 'Sales Support'
    C:\PS> Get-BrokerAppAssignmentPolicyRule -DesktopGroupUid $dg.Uid | Remove-BrokerAppAssignmentPolicyRule
    

Description  
\---\---\-----  
Deletes the application rule for the Sales Support desktop group from the site's assignment policy. This prevents any further machine assignments being made from this group, but it does not affect existing assignments made by the rule.