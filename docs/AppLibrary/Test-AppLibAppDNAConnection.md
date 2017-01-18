# Test-AppLibAppDNAConnection

Tests AppDNA connection.

## 语法

    Test-AppLibAppDNAConnection [-Address] <String> -Database <String> -UserName <String> -Password <SecureString> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Tests whether a connection to the configured AppDNA server can be made.

## 相关命令

- [Set-AppLibAppDNAConnection](Set-AppLibAppDNAConnection.html)
- [Remove-AppLibAppDNAConnection](Remove-AppLibAppDNAConnection.html)
- [Enable-AppLibAppDNAConnection](Enable-AppLibAppDNAConnection.html)
- [Enable-AppLibAppDNAConnection](Enable-AppLibAppDNAConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| 地址           | The URL to the AppDNA web server.                                                                                                                                      | true  | false |                                       |
| 数据库          | The AppDNA database identifier.                                                                                                                                        | true  | false |                                       |
| 用户名          | The username of the AppDNA user to connect with.                                                                                                                       | true  | false |                                       |
| 密码           | The AppDNA user's password.                                                                                                                                            | true  | false |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 字符串

### System.Security.SecureString The secure string representing the users password.

## 返回值

### 布尔型

## 示例

### 示例 1

    C:\PS>$SecurePassword =  ConvertTo-SecureString -String "passord" -AsPlainText -Force
                        C:\PS>Set-AppLibAppDNAConnection -Address "http://AppDNAServer.mydomain.net:8199/AppDNA" -Database "AppDNAServer:AppDNADB" -userName "AppDNAUser" -paassword $SecurePassword
    
                        True
    

Description  
\---\---\-----  
Tests whether a connection to be made to an AppDNA server with the credentials provided. In this example the connection was successful.

### 示例 2

    C:\PS>$SecurePassword =  ConvertTo-SecureString -String "passord" -AsPlainText -Force
                        C:\PS>Set-AppLibAppDNAConnection -Address "http://AppDNAServer.mydomain.net:8199/AppDNA" -Database "AppDNAServer:AppDNADB" -userName "AppDNAUser" -paassword $SecurePassword
    
                        False
                        Test-AppLibAppDNAConnection : An exception occurred.  The associated message was Unable to connect to the remote server
                        At line:1 char:1
                        + Test-AppLibAppDNAConnection -Address "http://AppDNAServer.mynetwork.net:8199/App ...
                        + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
                        + CategoryInfo          : InvalidOperation: (:) [Test-AppLibAppDNAConnection], InvalidOperationException
                        + FullyQualifiedErrorId : Citrix.XDPowerShell.Status.ExceptionThrown,Citrix.AppLibrary.Sdk.Commands.TestAppLibAppDNAConnectionCommand
    

Description  
\---\---\-----  
Tests whether a connection to be made to an AppDNA server with the credentials provided. In this example the connection was not successful.