# Get-EnvTestTask

Gets one or more EnvTestTask(s)

## 语法

    Get-EnvTestTask [-TaskId <Guid>] [-List] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns either the current task, a specified task, or list of tasks that are currently known to the EnvTest Service.

## 相关命令

- [Get-EnvTestDefinition](Get-EnvTestDefinition.html)
- [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition.html)
- [Start-EnvTestTask](Start-EnvTestTask.html)
- [Switch-EnvTestTask](Switch-EnvTestTask.html)
- [Stop-EnvTestTask](Stop-EnvTestTask.html)
- [Remove-EnvTestTask](Remove-EnvTestTask.html)
- [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata.html)
- [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata.html)

## 参数

| 名称           | 说明                                                                                                                       | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------ | ----- | ----- | ------------------------------------- |
| TaskId       | Specifies the task identifier to be returned. This value can be retrieved from an existing task's $task.TaskId property. | false | false |                                       |
| 列表           | List all running tasks, including the current one.                                                                       | false | false | false                                 |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                               | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.EnvTest.Sdk.EnvTestTask

A description of a previously started task.

## 示例

### 示例 1

    $currentTask = Get-EnvTestTask
    

Description  
\---\---\-----  
Retrieve the current task. The current task is the most recently created task unless Switch-EnvTestTask explicitly changes it.

### 示例 2

    $taskOfSpecificId = Get-EnvTestTask -TaskId 36C0EC52-2039-4D6E-B690-9F02F8CEFFCC
    

Description  
\---\---\-----  
Retrieve a fresh copy of a task object based on a known task id, which is always a Guid. This id can be retrieved from an existing task object via its $task.TaskId property.

### 示例 3

    $allKnownTasks = Get-EnvTestTask -List
    

Description  
\---\---\-----  
Retrieve the list of current tasks. This list includes any task started by the Start-EnvTestTask cmdlet since the service started that has not later been removed via Remove-EnvTestTask.