# Import-AdminRoleConfiguration

Imports role configuration data into the Delegated Administration Service.

## 语法

    Import-AdminRoleConfiguration [-Path] <String> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Import-AdminRoleConfiguration -Content <String> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This command is intended for use by Citrix Studio to import definitions, roles, permissions, and their mappings to operations.

The supplied configuration requires a digital signature; this is used to validate the integrity of the configuration.

## 相关命令

- [Get-AdminRoleConfiguration](Get-AdminRoleConfiguration.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| 路径           | The path to the file containing the role configuration data.                                                                                                           | true  | false          |                                       |
| 内容           | The content of the role configuration data.                                                                                                                            | true  | true (ByValue) |                                       |
| Force        | Allows older versions of role configuration to replace newer versions.                                                                                                 | false | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### 无

## Notes This command is supplied for infrastructure purposes only and is not intended for public use.

## 示例

### 示例 1

    C:\PS> Import-AdminRoleConfiguration -Path 'C:\MyAdminConfig.xml'
    

Description  
\---\---\-----  
Imports the contents of 'C:\MyAdminConfig.xml' to the Delegated Administration Service.