# Get-AdminEffectiveAdministrator

Retrieve the effective administrator objects for a user.

## 语法

    Get-AdminEffectiveAdministrator [-Name] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This command determines what groups the specified user belongs to and retrieves the matching administrator records. It includes the set of rights that would be granted to the user if he or she used the system.

As this command uses Active Directory to determine what groups the user has, the caller must have the ability to read this information from Active Directory.

Only enabled administrator records are returned.

## 相关命令

- [Get-AdminAdministrator](Get-AdminAdministrator.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| 名称           | User name or SID of user to query                          | true  | true (ByValue) |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 字符串

User name or SID of user to query

## 返回值

### Citrix.DelegatedAdmin.Sdk.Administrator

Administrator records matching the specified user

## 示例

### 示例 1

    C:\PS> Get-AdminEffectiveAdministrator MYDOMAIN\testuser
    

Description  
\---\---\-----  
Retrieve the administrator records matching user 'testuser'.