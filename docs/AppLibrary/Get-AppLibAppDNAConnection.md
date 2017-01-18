# Get-AppLibAppDNAConnection

Gets the AppDNA connection details.

## 语法

    Get-AppLibAppDNAConnection [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets the AppDNA Connection details used to integrate Citrix Studio with AppDNA.

## 相关命令

- [Set-AppLibAppDNAConnection](Set-AppLibAppDNAConnection.html)
- [Remove-AppLibAppDNAConnection](Remove-AppLibAppDNAConnection.html)
- [Enable-AppLibAppDNAConnection](Enable-AppLibAppDNAConnection.html)
- [Disable-AppLibAppDNAConnection](Disable-AppLibAppDNAConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

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

## Notes The AppDNA user's password is never returned with the connection details.

## Examples

### EXAMPLE 1

    C:\PS>Get-AppLibAppDNAConnection
    
                        Address  : http://AppDNAServer.mynetwork.net:8199/AppDNA
                        Database : AppDNAServer:AppDNADB
                        Enabled  : True
                        UserName : AppDNAUser
    

Description  
\---\---\-----  
Gets the AppDNA Connection details used to integrate Citrix Studio with AppDNA.