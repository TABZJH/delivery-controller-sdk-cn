# Set-MonitorNotificationEmailServerConfiguration

Saves a new email server configuration

## 语法

    Set-MonitorNotificationEmailServerConfiguration [-InputObject] <MonitorNotificationEmailServerConfiguration> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-MonitorNotificationEmailServerConfiguration -ProtocolType <EmailProtocolType> -ServerName <String> -PortNumber <Int32> -SenderEmailAddress <String> -RequiresAuthentication <Boolean> [-Credential <PSCredential>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The saved configuration describes the new settings to be used to send emails

## 相关命令

- [Get-MonitorNotificationEmailServerConfiguration](Get-MonitorNotificationEmailServerConfiguration.html)

## 参数

| 名称                     | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| InputObject            | Configuration object to persist                                                                                                                                        | true  | false |                                       |
| ProtocolType           | Email protocol type. Possible values are Smtp SmtpSsl SmtpTls                                                                                                          | true  | false |                                       |
| 服务器名称                  | Email server name                                                                                                                                                      | true  | false |                                       |
| PortNumber             | Email server port number                                                                                                                                               | true  | false |                                       |
| SenderEmailAddress     | Sender’s email address                                                                                                                                                 | true  | false |                                       |
| RequiresAuthentication | Whether the server requires authentication                                                                                                                             | true  | false |                                       |
| 凭据                     | Configuration credential                                                                                                                                               | false | false |                                       |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### MonitorNotificationEmailServerConfiguration

The saved configuration

## 示例

### 示例 1

    $secpasswd = ConvertTo-SecureString "PasswordHere" -AsPlainText -Force
              $mycreds = New-Object System.Management.Automation.PSCredential ("username", $secpasswd)
    
              Set-MonitorNotificationEmailServerConfiguration -ProtocolType Smtp -ServerName "mail.citrix.com" -PortNumber 1111 -SenderEmailAddress "user1@abc.com" -RequiresAuthentication $true -Credential $mycreds
    

Description  
\---\---\-----  
Set new email server configration using the specified parameters