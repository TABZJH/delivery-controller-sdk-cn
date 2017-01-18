# Stop-EnvTestTask

Stops a still running task from completing.

## 语法

    Stop-EnvTestTask [-TaskId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Stop-EnvTestTask [-Task <EnvTestTask>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Stops a still running task from completing. A task may still be retreived via Get-EnvTestTask until it Remove-EnvTestTask is called with its task id.

## 相关命令

- [Get-EnvTestDefinition](Get-EnvTestDefinition.html)
- [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition.html)
- [Get-EnvTestTask](Get-EnvTestTask.html)
- [New-EnvTestTask](New-EnvTestTask.html)
- [Start-EnvTestTask](Start-EnvTestTask.html)
- [Switch-EnvTestTask](Switch-EnvTestTask.html)
- [Remove-EnvTestTask](Remove-EnvTestTask.html)
- [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata.html)
- [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata.html)

## 参数

| 名称           | 说明                                                                       | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ------------------------------------------------------------------------ | ----- | -------------- | ------------------------------------- |
| TaskId       | The id of the task to stop, retrieveable from the $task.TaskId property. | false | false          |                                       |
| 任务           | An EnvTestTask representing the task to stop                             | false | true (ByValue) |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。               | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    Stop-EnvTestTask
    

Description  
\---\---\-----  
Stops the current task from completing if it is still running.

### 示例 2

    Stop-EnvTestTask -TestId 50A4139F-2B55-4A97-A1BE-20EE4E124AA3
    

Description  
\---\---\-----  
Stops a task from completing via its id, which is available from an existing task's $task.TaskId property.

### 示例 3

    $secondTask = $(Get-EnvTestTask -List)[1]
    Stop-EnvTestTask -Task $secondTask
    

Description  
\---\---\-----  
Stops the second task in the list returned by Get-EnvTestTask -List.