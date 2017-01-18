# Test-BrokerAssignmentPolicyRuleNameAvailable

Determine whether the proposed AssignmentPolicyRule Name is available for use.

## 语法

    Test-BrokerAssignmentPolicyRuleNameAvailable [-Name] <String[]> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet checks whether proposed AssignmentPolicyRule Name is available for use. It returns a record for each Name indicating the availability of that Name, with $true indicating that the Name is unused and available for use, or $false if it is not available.

## 相关命令

- [Get-BrokerAssignmentPolicyRule](Get-BrokerAssignmentPolicyRule.html)
- [New-BrokerAssignmentPolicyRule](New-BrokerAssignmentPolicyRule.html)
- [Rename-BrokerAssignmentPolicyRule](Rename-BrokerAssignmentPolicyRule.html)

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入                           | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | -------------------------------------------------------------------------------------- |
| 名称           | The AssignmentPolicyRule Name to be tested.                                                                                                        | true  | true (ByValue, ByPropertyName) |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false                          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### System.String

You can pipe a string that contains the Name to test.

## 返回值

### Citrix.Broker.Admin.SDK.NameAvailability

The cmdlet returns a result for each Name specified. An availability of "True" indicates the Name is available for use, and "False" if it is not available.

## 示例

### 示例 1

    C:\PS> Test-BrokerAssignmentPolicyRuleNameAvailable -Name Test1
    

Description  
\---\---\-----  
Checks whether the Name "Test1" is available.

### 示例 2

    C:\PS> Test-BrokerAssignmentPolicyRuleNameAvailable @("Test1","Test2","Test3")
    

Description  
\---\---\-----  
Checks whether each of the specified names is available.