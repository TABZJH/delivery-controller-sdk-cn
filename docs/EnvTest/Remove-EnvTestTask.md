# Remove-EnvTestTask

Removes from the database completed tasks for the EnvTest Service.

## 语法

    Remove-EnvTestTask [-TaskId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-EnvTestTask [-Task <EnvTestTask>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Enables completed tasks that have run within the EnvTest Service to be removed from the database.

## 相关命令

- [Get-EnvTestDefinition](Get-EnvTestDefinition.html)
- [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition.html)
- [Get-EnvTestTask](Get-EnvTestTask.html)
- [Start-EnvTestTask](Start-EnvTestTask.html)
- [Switch-EnvTestTask](Switch-EnvTestTask.html)
- [Stop-EnvTestTask](Stop-EnvTestTask.html)
- [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata.html)
- [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata.html)

## 参数

| 名称           | 说明                                                                                               | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ------------------------------------------------------------------------------------------------ | ----- | -------------- | ------------------------------------- |
| TaskId       | Specifies the identifier of the task to be removed, retrieveable from the $task.TaskId property. | false | false          |                                       |
| 任务           | Specifies the task to be removed.                                                                | false | true (ByValue) |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                       | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    Remove-EnvTestTask
    

Description  
\---\---\-----  
Removes the current task from the EnvTest service.

### 示例 2

    Remove-EnvTestTask -TaskId 50A4139F-2B55-4A97-A1BE-20EE4E124AA3
    

Description  
\---\---\-----  
Removes a task from the EnvTest service via its id, which is available from an existing task's $task.TaskId property.

### 示例 3

    $secondTask = $(Get-EnvTestTask -List)[1]
    Remove-EnvTestTask -Task $secondTask
    

Description  
\---\---\-----  
Removes the second task in the list returned by Get-EnvTestTask -List.