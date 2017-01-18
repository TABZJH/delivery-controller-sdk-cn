# Set-AppLibAppDNAConnection

Sets the connection details for integration of AppDNA into AppLibrary to allow AppDNA Analysis by this site.

## 语法

    Set-AppLibAppDNAConnection [-Address] <String> -Database <String> -UserName <String> -Password <SecureString> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Sets the connection details for integration of AppDNA into AppLibrary to allow AppDNA Analysis of AppDisk, Machines and DesktopGroups.

## 相关命令

- [Get-AppLibAppDNAConnection](Get-AppLibAppDNAConnection.html)
- [Remove-AppLibAppDNAConnection](Remove-AppLibAppDNAConnection.html)
- [Enable-AppLibAppDNAConnection](Enable-AppLibAppDNAConnection.html)
- [Deisable-AppLibAppDNAConnection](Deisable-AppLibAppDNAConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| 地址           | The URL to the AppDNA web server.                                                                                                                                      | true  | false |                                       |
| 数据库          | The AppDNA database identifier.                                                                                                                                        | true  | false |                                       |
| 用户名          | The username of the AppDNA user to connect with.                                                                                                                       | true  | false |                                       |
| 密码           | The AppDNA user's password                                                                                                                                             | true  | false |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 字符串

### System.Security.SecureString The secure string representing the user's password.

## 返回值

### Citrix.AppLibrary.Sdk.AppDNAConnection  
This object provides details of the AppDNA Connection and contains the following information:  
Address <string>  
The URL of the AppDNA web server.  
Database <string>  
The database identifier from the AppDNA site  
Enabled <bool>  
Whether or not the connection is enabled  
Username <string>  
The user account name used to make the connection.

## Notes The AppDNA user's password is stored securely and is never returned in the AppDNAConnection object.  
Only one AppDNA configuration can be stored. If a connection is already set up, the connection details will be replaced.  
The connection will be enabled by default in the AppLibrary when the details are set.

## Examples

### EXAMPLE 1

    C:\PS>$SecurePassword = ConvertTo-SecureString -String "password" -AsPlainText -Force
                        C:\PS>Set-AppLibAppDNAConnection -Address "http://my.appdna.server:8199/AppDNA" -Database "localhost:AppDNADB" -userName "AppDNAUser" -password $SecurePassword
    
                        Address  : http://my.appdna.server:8199/AppDNA
                        Database : localhost:AppDNADB
                        Enabled  : True
                        UserName : AppDNAUser
    

Description  
\---\---\-----  
Sets the AppLibrary AppDNA connection to the configuration localhost:AppDNADB on my.appdna.server under the "AppDNAUser" account.