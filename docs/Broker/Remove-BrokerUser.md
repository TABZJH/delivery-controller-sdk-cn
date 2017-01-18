# Remove-BrokerUser

Remove broker user objects from another broker object

## 语法

    Remove-BrokerUser [-InputObject] <User[]> [-ApplicationGroup <ApplicationGroup>] [-Application <Application>] [-SessionLinger <SessionLinger>] [-SessionPreLaunch <SessionPreLaunch>] [-Machine <Machine>] [-PrivateDesktop <PrivateDesktop>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerUser [-Name] <String> [-ApplicationGroup <ApplicationGroup>] [-Application <Application>] [-SessionLinger <SessionLinger>] [-SessionPreLaunch <SessionPreLaunch>] [-Machine <Machine>] [-PrivateDesktop <PrivateDesktop>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerUser cmdlet removes broker user objects from another specified object, such as a broker private desktop, to which the user had previously been added.

## 相关命令

- [Add-BrokerUser](Add-BrokerUser.html)
- [Get-BrokerUser](Get-BrokerUser.html)

## 参数

| 名称               | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject      | Specifies the user objects to remove.                                                                                                                                           | true  | true (ByValue)        |                                                                                        |
| 名称               | Specifies the user objects to remove, based on their Name property.                                                                                                             | true  | true (ByPropertyName) | 空值                                                                                     |
| ApplicationGroup | The application group from which to remove the user                                                                                                                             | false | true (ByValue)        |                                                                                        |
| 应用程序             | The application from which to remove the user                                                                                                                                   | false | true (ByValue)        |                                                                                        |
| SessionLinger    | The desktop group session linger setting from which to remove the user.                                                                                                         | false | true (ByValue)        | 空值                                                                                     |
| SessionPreLaunch | The desktop group session pre-launch setting from which to remove the user.                                                                                                     | false | true (ByValue)        | 空值                                                                                     |
| 计算机              | The machine from which to remove the user                                                                                                                                       | false | true (ByValue)        | 空值                                                                                     |
| PrivateDesktop   | The desktop from which to remove the user                                                                                                                                       | false | true (ByValue)        | 空值                                                                                     |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.USer

You can pipe the users to be removed to Remove-BrokerUser.

## 返回值

### 无

## Notes Specify one of the -Machine or -PrivateDesktop parameters only.

## 示例

### 示例 1

    Remove-BrokerUser "DOMAIN\UserName" -PrivateDesktop "DOMAIN\MachineName"
    

Description  
\---\---\-----  
Remove the assignment of the specified private desktop to the specified user.