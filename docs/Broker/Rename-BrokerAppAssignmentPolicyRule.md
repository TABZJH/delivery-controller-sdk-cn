# Rename-BrokerAppAssignmentPolicyRule

Renames an application rule in the site's assignment policy.

## 语法

    Rename-BrokerAppAssignmentPolicyRule [-InputObject] <AppAssignmentPolicyRule[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerAppAssignmentPolicyRule [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerAppAssignmentPolicyRule cmdlet renames an application rule in the site's assignment policy. The Name property of the rule is changed.

An application rule in the assignment policy defines the users who are entitled to a self-service persistent machine assignment from the rule's desktop group; once assigned the machine can run one or more applications published from the group.

## 相关命令

- [New-BrokerAppAssignmentPolicyRule](New-BrokerAppAssignmentPolicyRule.html)
- [Get-BrokerAppAssignmentPolicyRule](Get-BrokerAppAssignmentPolicyRule.html)
- [Set-BrokerAppAssignmentPolicyRule](Set-BrokerAppAssignmentPolicyRule.html)
- [Remove-BrokerAppAssignmentPolicyRule](Remove-BrokerAppAssignmentPolicyRule.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                    | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The application rule in the assignment policy to be renamed.                                                                                                                                                          | true  | true (ByValue)        |                                                                                        |
| 名称           | The existing name of the application rule in the assignment policy to be renamed.                                                                                                                                     | true  | true (ByPropertyName) |                                                                                        |
| NewName      | The new name of the application rule in the assignment policy being renamed. The new name must not match that of any other existing rule in the policy (irrespective of whether it is a desktop or application rule). | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                        | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                       | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                    | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.AppAssignmentPolicyRule

The application rule in the assignment policy being renamed.

## 返回值

### None or Citrix.Broker.Admin.SDK.AppAssignmentPolicyRule

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AppAssignmentPolicyRule object.

## 示例

### 示例 1

    C:\PS> Rename-BrokerAppAssignmentPolicyRule 'Offshore' -NewName 'Remote Workers'
    

Description  
\---\---\-----  
Renames the application rule in the assignment policy called Offshore to Remote Workers. The new name of the rule must be unique in the assignment policy.