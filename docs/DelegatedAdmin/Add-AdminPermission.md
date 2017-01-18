# Add-AdminPermission

Add permissions to the set of permissions of a role.

## 语法

    Add-AdminPermission [-InputObject] <Permission[]> -Role <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-AdminPermission [-Permission] <String[]> -Role <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Add extra permissions to the set of permissions that a role maps to.

Any administrator with a right including that role immediately gains the ability to use the operations of the new permissions.

Duplicate permissions do not produce an error, and permissions are skipped if the role already contains the permission (without error).

You cannot modify the permissions of built-in roles.

## 相关命令

- [Remove-AdminPermission](Remove-AdminPermission.html)
- [Get-AdminPermission](Get-AdminPermission.html)
- [Get-AdminRole](Get-AdminRole.html)
- [Get-AdminPermissionGroup](Get-AdminPermissionGroup.html)
- [Test-AdminAccess](Test-AdminAccess.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the permissions to add.                                                                                                                                      | true  | true (ByValue)        |                                       |
| 权限           | Specifies the list of permissions to add (by identifier).                                                                                                              | true  | true (ByPropertyName) |                                       |
| 角色           | Role name or identifier of the role to update.                                                                                                                         | true  | false                 |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Permission

You can pipe a list of permissions to be added into this command.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Add-AdminPermission -Role MyRole -Permission Global_Read,Logging_Read
    

Description  
\---\---\-----  
Add a couple of specific permissions to the 'MyRole' role.

### 示例 2

    C:\PS> $list = Get-AdminRole "Delivery Administrator" | Select -Expand Permissions
    C:\PS> Add-AdminPermission -Role MyRole -Permission $list
    

Description  
\---\---\-----  
Add all of the permissions of the Delivery Administrator role to MyRole.