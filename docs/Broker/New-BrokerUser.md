# New-BrokerUser

Creates a new broker user object

## 语法

    New-BrokerUser [-SID] <SecurityIdentifier> [-AdminAddress <String>] [<CommonParameters>]
    
    New-BrokerUser [-Name] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The New-BrokerUser cmdlet creates a new broker object to represent a user identity (or the identity of a group of users). The object is created local to the PowerShell environment in which the cmdlet is run; no new user object is created in the broker configuration, unless the object is added to another broker object, such as a machine or a desktop. For details, see Add-BrokerUser.

The identity of the user or group must be specified using either the Name or SID parameter

## 相关命令

- [Add-BrokerUser](Add-BrokerUser.html)
- [Get-BrokerUser](Get-BrokerUser.html)
- [Remove-BrokerUser](Remove-BrokerUser.html)

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| SID          | The SID of the user or group                                                                                                                       | true  | false | 空值                                                                                     |
| 名称           | The name of the user or group                                                                                                                      | true  | false | 空值                                                                                     |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.User

The broker user object## Notes Typically, broker user objects are created implicitly using the Add-BrokerUser cmdlet with a user name or SID.

## 示例

### 示例 1

    $user = New-BrokerUser DOMAIN\UserName
    

Description  
\---\---\-----  
Create a broker user object for the specified user.

### 示例 2

    $user = New-BrokerUser -SID S-1-5-23-1763203430-193137401-908696819-3450
    

Description  
\---\---\-----  
Create a broker user object for the specified user.