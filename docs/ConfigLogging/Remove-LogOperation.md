# Remove-LogOperation

Deletes configuration logs

## 语法

    Remove-LogOperation -DatabaseCredentials <PSCredential> [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-IncludeIncomplete] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-LogOperation -UserName <String> [-Password <String>] [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-IncludeIncomplete] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-LogOperation -UserName <String> -SecurePassword <SecureString> [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-IncludeIncomplete] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Remove-LogOperation deletes logs from the Configuration Logging database. This cmdlet targets high level operation logs for deletion. The associated low level operations logs are deleted as part of this operation via cascade deletion functionality present in the configuration logging database schema.

## 相关命令

- [](.html)

## 参数

| 名称                  | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| DatabaseCredentials | Specifies the credentials of a database user with permission to delete records from the Configuration Logging database.                                                | true  | false |                                       |
| 用户名                 | Specifies the user name of a database user with permission to delete records from the Configuration Logging database.                                                  | true  | false |                                       |
| SecurePassword      | Specifies the password a database user, in secure string form, with permission to delete records from the Configuration Logging database.                              | true  | false |                                       |
| 密码                  | Specifies the password of a database user with permission to delete records from the Configuration Logging database.                                                   | false | false |                                       |
| StartDateRange      | Specifies the start time of the earliest high level operation to delete                                                                                                | false | false | DateTime.Min                          |
| EndDateRange        | Specifies the end time of the latest high level operation to delete                                                                                                    | false | false | DateTime.UtcNow                       |
| IncludeIncomplete   | Specifies if incomplete high level operations should be deleted.                                                                                                       | false | false |                                       |
| LoggingId           | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress        | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    C:\PS> Remove-LogOperation  -UserName "DOMAIN\User"  -Password "UserPassword"
    

Description  
\---\---\-----  
Remove all completed operation logs

### 示例 2

    C:\PS> Remove-LogOperation  -UserName "DOMAIN\User"  -Password "UserPassword" -IncludeIncomplete
    

Description  
\---\---\-----  
Remove all operations

### 示例 3

    C:\PS> Remove-LogOperation -username "domain\userName" -password "password" -StartDateRange "2013-01-01 12:00:00"  -EndDateRange "2013-01-31 12:00:00"
    

Description  
\---\---\-----  
Delete logs started on or after "2013-01-01 12:00:00" and completed on or before "2013-01-31 12:00:00"

### 示例 4

    C:\PS> $securePassword = ConvertTo-SecureString -String "UserPassword" -AsPlainText -Force
    C:\PS> $credentials    = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList "DOMAIN\UserName", $securePassword
    C:\PS> Remove-LogOperation -StartDateRange -DatabaseCredentials $credentials
    

Description  
\---\---\-----  
Delete logs by supplying database user credentials via a credentials object.