# Switch-EnvTestTask

Sets the current task that will be returned by a call to Get-EnvTestTask with no parameters.

## 语法

    Switch-EnvTestTask [-TaskId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Switch-EnvTestTask [-Task <EnvTestTask>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Sets the current task that will be returned by a call to Get-EnvTestTask with no parameters.

## 相关命令

- [Get-EnvTestDefinition](Get-EnvTestDefinition.html)
- [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition.html)
- [Get-EnvTestTask](Get-EnvTestTask.html)
- [New-EnvTestTask](New-EnvTestTask.html)
- [Start-EnvTestTask](Start-EnvTestTask.html)
- [Stop-EnvTestTask](Stop-EnvTestTask.html)
- [Remove-EnvTestTask](Remove-EnvTestTask.html)
- [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata.html)
- [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata.html)

## 参数

| 名称           | 说明                                                                               | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | -------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| TaskId       | Specifies the identifier of the task to be made current.                         | false | false |                                       |
| 任务           | The task object to be made current, retrieveable from the $task.TaskId property. | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                       | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.Management.Automation.PSObject

Objects containing the TaskId parameter can be piped to the Remove-EnvTestTask command.

## 返回值

### 

## 示例

### 示例 1

    Switch-EnvTestTask -TaskId 50A4139F-2B55-4A97-A1BE-20EE4E124AA3
    

Description  
\---\---\-----  
Switches the current task to another via its id, which is available from an existing task's $task.TaskId property.

### 示例 2

    $secondTask = $(Get-EnvTestTask -List)[1]          
    Switch-EnvTestTask -Task $switchTask
    

Description  
\---\---\-----  
Switches the current task to the second in the list returned by Get-EnvTestTask -List.