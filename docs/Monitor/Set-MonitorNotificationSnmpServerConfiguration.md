# Set-MonitorNotificationSnmpServerConfiguration

Saves a new Snmp server configuration

## 语法

    Set-MonitorNotificationSnmpServerConfiguration [-InputObject] <MonitorNotificationSnmpServerConfiguration> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-MonitorNotificationSnmpServerConfiguration [-ServerName <String>] [-PortNumber <Int32>] [-SnmpSender <String>] [-EngineId <String>] [-AuthPassword <SecureString>] [-PrivPassword <SecureString>] [-PrivPasswordProtocol <PrivacyProtocolType>] [-AuthPasswordProtocol <AuthProtocolType>] [-CommunityString <String>] [-Protocol <SnmpProtocolType>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The saved configuration describes the new settings to be used to send Snmps

## 相关命令

- [Get-MonitorNotificationSnmpServerConfiguration](Get-MonitorNotificationSnmpServerConfiguration.html)

## 参数

| 名称                   | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| InputObject          | Configuration object to persist                                                                                                                                        | true  | false |                                       |
| 服务器名称                | Snmp listener server name                                                                                                                                              | false | false |                                       |
| PortNumber           | Snmp server port number                                                                                                                                                | false | false |                                       |
| SnmpSender           | Sender’s Name                                                                                                                                                          | false | false |                                       |
| EngineId             | Engine ID                                                                                                                                                              | false | false |                                       |
| AuthPassword         | Password used for authentication                                                                                                                                       | false | false |                                       |
| PrivPassword         | Password used for encryption                                                                                                                                           | false | false |                                       |
| PrivPasswordProtocol | Protocol used for encryption                                                                                                                                           | false | false |                                       |
| AuthPasswordProtocol | Protocol used for hash Authentication                                                                                                                                  | false | false |                                       |
| CommunityString      | Comunity String for SNMP V2                                                                                                                                            | false | false |                                       |
| 协议                   | Snmp protocol used for trap                                                                                                                                            | false | false |                                       |
| LoggingId            | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress         | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### MonitorNotificationSnmpServerConfiguration

The saved configuration

## 示例

### 示例 1

    Set-MonitorNotificationSnmpServerConfiguration -ServerName "192.168.100.100" -PortNumber 162 -SnmpSender directoradmin -AuthPassword authpassword -AuthPasswordProtocol MD5 -PrivatePassword PrivPassword -PrivatePasswordProtocol DES
    

Description  
\---\---\-----  
Set new Snmp server configration using the specified parameters