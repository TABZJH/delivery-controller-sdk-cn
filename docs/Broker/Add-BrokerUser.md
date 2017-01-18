# Add-BrokerUser

在用户与另一个代理对象之间创建关联

## 语法

    Add-BrokerUser [-InputObject] <User[]> [-ApplicationGroup <ApplicationGroup>] [-Application <Application>] [-SessionLinger <SessionLinger>] [-SessionPreLaunch <SessionPreLaunch>] [-Machine <Machine>] [-PrivateDesktop <PrivateDesktop>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-BrokerUser [-Name] <String> [-ApplicationGroup <ApplicationGroup>] [-Application <Application>] [-SessionLinger <SessionLinger>] [-SessionPreLaunch <SessionPreLaunch>] [-Machine <Machine>] [-PrivateDesktop <PrivateDesktop>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Add-BrokerUser cmdlet 向另一个指定对象（如代理专用桌面）添加代理用户对象。 This depends on the target object type: o Machine - assign the broker machine to the specified user(s); when the machine is subsequently added to a desktop group, the desktop is also assigned to the same user(s). o PrivateDesktop - assign the desktop to the specified user(s). o Application - assign the application to the specified user(s). o Application group - assign the applications in the application group to the specified user(s).

## 相关命令

- [Get-BrokerUser](Get-BrokerUser.html)
- [Remove-BrokerUser](Remove-BrokerUser.html)

## 参数

| 名称               | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject      | 要添加的用户对象。                                                                                                                                                                       | true  | true (ByValue)        | 空值                                                                                     |
| 名称               | 要添加的一个或多个用户的名称。                                                                                                                                                                 | true  | true (ByPropertyName) | 空值                                                                                     |
| ApplicationGroup | The application group to which the user is to be assigned.                                                                                                                      | false | true (ByValue)        |                                                                                        |
| 应用程序             | The application to which the user is to be assigned.                                                                                                                            | false | true (ByValue)        |                                                                                        |
| SessionLinger    | 要分配给用户的会话延迟设置。                                                                                                                                                                  | false | true (ByValue)        | 空值                                                                                     |
| SessionPreLaunch | 要分配给用户的会话预启动设置。                                                                                                                                                                 | false | true (ByValue)        | 空值                                                                                     |
| 计算机              | 要分配给用户的计算机                                                                                                                                                                      | false | true (ByValue)        | 空值                                                                                     |
| PrivateDesktop   | 要分配给用户的桌面                                                                                                                                                                       | false | true (ByValue)        | 空值                                                                                     |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.USer

You can pipe the users to be added to Add-BrokerUser.

## 返回值

### 无

## Notes Specify one of the -Machine or -PrivateDesktop or -Application parameters only.

## 示例

### 示例 1

    Add-BrokerUser "DOMAIN\UserName" -PrivateDesktop "DOMAIN\MachineName"
    

Description  
\---\---\-----  
Assign the specified private desktop to the specified user.

### 示例 2

    Add-BrokerUser "DOMAIN\UserName" -Application "ApplicationName"
    

Description  
\---\---\-----  
Assign the specified application to the specified user.