# Remove-BrokerSessionPreLaunch

Removes a session pre-launch setting.

## 语法

    Remove-BrokerSessionPreLaunch [-InputObject] <SessionPreLaunch[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerSessionPreLaunch [-DesktopGroupName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerSessionPreLaunch cmdlet is used to delete an existing session pre-launch setting.

## 相关命令

- [New-BrokerSessionPreLaunch](New-BrokerSessionPreLaunch.html)
- [Get-BrokerSessionPreLaunch](Get-BrokerSessionPreLaunch.html)
- [Set-BrokerSessionPreLaunch](Set-BrokerSessionPreLaunch.html)

## 参数

| 名称               | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject      | The session pre-launch setting to be deleted.                                                                                                                                   | true  | true (ByValue)        |                                                                                        |
| DesktopGroupName | The name of the desktop group whose session pre-launch setting is to be removed.                                                                                                | true  | true (ByPropertyName) |                                                                                        |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.SessionPreLaunch

Session pre-launch settings may be specified through pipeline input.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Get-BrokerSessionPreLaunch | Remove-BrokerSessionPreLaunch
    

Description  
\---\---\-----  
Deletes every session pre-launch setting for all desktop groups.